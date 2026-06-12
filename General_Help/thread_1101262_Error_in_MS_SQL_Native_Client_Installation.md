---
title: "Error in MS SQL Native Client Installation"
date: 2009-03-20
forum: General Help
---

### Post by gunaksg on 2009-03-20
MS SQL Native Client installation

Getting following Error :

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

---

