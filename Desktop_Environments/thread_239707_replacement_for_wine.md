---
title: "replacement for wine?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by njzillest on 2006-08-19
Wine doesnt work for me, i keep on getting an error

```

njzillest@njzillest-laptop:~$ wine /home/njzillest/Desktop/pop3.exe
err:module:import_dll Library cygwin1.dll (which is needed by L"Z:\\home\\njzillest\\Desktop\\pop3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\njzillest\\Desktop\\pop3.exe" failed, status c0000135

```

Is there a nother windows emulator (or non emulator) that will help me run simple .exes?

That .exe is from C source that i compiled on windows. Its no longer than 75 lines.

---

### Post by taurus on 2006-08-19
Run an emulator like VMware or qemu if you wish...

---

### Post by njzillest on 2006-08-19
what version should i get, i see two free ones- server and SDK/API

can you tell me whats the difference?

thanks

---

### Post by Steven_B on 2006-08-19
It looks like you're trying to use a dll (from Cygwin) which wine doesn't have.  You could try copying Cygwin's dll to somewhere wine can read it.
I haven't done this myself, but I know it is possible.  From what I understand, a real emulator requires a licened copy of Windows, and runs much slower.

---

