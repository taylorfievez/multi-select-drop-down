# Multi-select dropdown

Description: VBA code for creating a multi-select dropdown list in Excel. 

Private Sub Worksheet_Change(ByVal Target As Range)
Dim Oldvalue As String
Dim Newvalue As String
Application.EnableEvents = True
On Error GoTo Exitsub
If Target.Address = "$A$10" Or Target.Address = "$D$10" Then
  If Target.SpecialCells(xlCellTypeAllValidation) Is Nothing Then
    GoTo Exitsub
  Else: If Target.Value = "" Then GoTo Exitsub Else
    Application.EnableEvents = False
    Newvalue = Target.Value
    Application.Undo
    Oldvalue = Target.Value
      If Oldvalue = "" Then
        Target.Value = Newvalue
      Else
        If InStr(1, Oldvalue, Newvalue) = 0 Then
            Target.Value = Oldvalue & vbNewLine & Newvalue
      Else:
        Target.Value = Oldvalue
      End If
    End If
  End If
End If
Application.EnableEvents = True
Exitsub:
Application.EnableEvents = True
End Sub
