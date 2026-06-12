---
title: "steaminstaller.exe"
date: 2009-01-04
forum: General Help
---

### Post by JLoomis95 on 2009-01-04
Anyone got a link to steaminstaller.exe?

---

### Post by Ahadiel on 2009-01-04
[http://cdn.steampowered.com/download/SteamInstall.msi](http://cdn.steampowered.com/download/SteamInstall.msi)
And assuming you plan on installing it with wine
```
wine msiexec /i SteamInstall.msi
```

---

### Post by JLoomis95 on 2009-01-04
ya i tired using that command but i keep getting this

[HTML]justin@desktop:~/Desktop$ wine msiexec /i SteamInstall.msi
fixme:sfc:SfcIsKeyProtected ((nil), (null)) stub
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x32e4b0,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x134ed0,(nil)): stub
err:eventlog:ReportEventW L"=====================================================\r\nException code: C0000005 ACCESS_VIOLATION\r\nFunction: 0x0\r\n=====================================================\r\n\r\nRegisters:\r\nEAX:00000000  EBX:004BEF2D  ECX:0032E4EC  EDX:00000031  ESI:0032E674  EDI:00000000\r\nCS:EIP:0023:00000000 "...
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
[/HTML]

---

### Post by gunaksg on 2009-03-20
I m also getting same kind of error while installing sqlncli.msi 

Following error 
-------------------------------------------------------------------
subhiksha@subhiksha:~/Desktop/SQL NC$ wine msiexec.exe /i sqlncli.msi 
fixme:sfc:SFC_3 0
fixme:netapi32:NetGetJoinInformation Stub (null) 0x56e21c 0x56e210
fixme:advapi:CheckTokenMembership (0x94 0x135f30 0x56de14) stub!
fixme:advapi:SaferCreateLevel (1, 40000, 1, 0x56e31c, (nil)) stub
fixme:advapi:RegisterEventSourceW ((null),L"MsiInstaller"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003f0,0x135f30,0x0007,0x00000000,0x56daac,(nil)): stub
err:eventlog:ReportEventW L"Z:\\home\\subhiksha\\Desktop\\SQL NC\\sqlncli.msi"
err:eventlog:ReportEventW L"(NULL)"
err:eventlog:ReportEventW L"(NULL)"
err:eventlog:ReportEventW L"(NULL)"
err:eventlog:ReportEventW L"(NULL)"
err:eventlog:ReportEventW (null)
err:eventlog:ReportEventW (null)
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
The system administrator has set policies to prevent this installation.


Any one help me out from this problem..

---

