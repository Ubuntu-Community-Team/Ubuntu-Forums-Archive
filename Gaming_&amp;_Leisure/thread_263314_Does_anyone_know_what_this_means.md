---
title: "Does anyone know what this means?"
date: 2006-09-23
forum: Gaming &amp; Leisure
---

### Post by threethirty on 2006-09-23
```
three@CondorV2:~$ wine /home/three/.wine/drive_c/Program_Files/EA_Games/Battlefield_Vietnam/bfvietnam.exe
three@CondorV2:~$ wine /home/three/.wine/drive_c/Program_Files/EA_Games/Battlefield_Vietnam/
wine: could not load L"C:\\Program_Files\\EA_Games\\Battlefield_Vietnam\\.": Invalid handle
three@CondorV2:~$ cd /home/three/.wine/drive_c/Program_Files/EA_Games/Battlefield_Vietnam/
three@CondorV2:~/.wine/drive_c/Program_Files/EA_Games/Battlefield_Vietnam$ wine bfvietnam.exe
fixme:advapi:QueryServiceObjectSecurity 0x192210 4 0x33ca30 512 0x33ce40
fixme:advapi:SetServiceObjectSecurity 0x192210 4 0x33cc30
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
three@CondorV2:~/.wine/drive_c/Program_Files/EA_Games/Battlefield_Vietnam$

```

any ideas?

---

### Post by Matrix101 on 2006-09-23
It seems to be an issue with the copy-protection of BFV. Maybe you should try this [http://www.liflg.org/?catid=7&gameid=20](http://www.liflg.org/?catid=7&gameid=20)

---

