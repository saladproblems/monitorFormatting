# monitorFormatting
Example of using format and extension files to format monitor output

How to use these files:

  Update-FormatData -PrependPath C:\Temp\monitor.ps1xml
  Update-TypeData -PrependPath C:\Temp\monitorTypeExt.ps1xml
  Get-CimInstance -ClassName WmiMonitorID -Namespace root\wmi

Why would you want to do this?

You can lose a lot of functionality when you change an object type. For example, this won't work because Invoke-CimMethod expects a ciminstance, not the pscustomobject Select-Object outputs:

  Get-CimInstance win32_process -Filter 'name = "notepad.exe"' | select * | Invoke-CimMethod -MethodName terminate

Additionally, lots of objects in powershell have methods to save, stop, start, edit, trim, etc., and those are lost as well when you convert the object type with select and formatting commands.
