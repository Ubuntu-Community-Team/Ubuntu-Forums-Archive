---
title: "steaminstaller"
date: 2009-01-04
forum: General Help
---

### Post by JLoomis95 on 2009-01-04
Hey, im trying to install steam and when i run the installer this happens...

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

Any clue how to fix this?

---

