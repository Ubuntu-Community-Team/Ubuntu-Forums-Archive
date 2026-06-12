---
title: "wine problem"
date: 2005-10-13
forum: Desktop Environments
---

### Post by lostdata on 2005-10-13
when i try to run wine after installing from winehq repositories its failing 

```

lostdata@UPE:~$ wine
wine: creating configuration directory '/home/lostdata/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/lostdata/.wine'.
lostdata@UPE:~$ sudo wine
wine: creating configuration directory '/home/lostdata/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/lostdata/.wine'.

```

any ideas on how i could fix this would be appriciated... i just installed a fresh copy of breezey final...

---

### Post by lostdata on 2005-10-13
nevermind

apt-get install libstdc++5

resolved the problem

---

