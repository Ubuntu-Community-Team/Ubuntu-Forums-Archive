---
title: "wine can't seem to find the dlls that are inside the application directory."
date: 2005-11-21
forum: Desktop Environments
---

### Post by fragmental on 2005-11-21
If I try to run a complex windows applications such as games or..well, any application I tried to run besides sol.exe, it spits out errors about not being able to find dlls.  On closer examination it seems that all those libraries are sitting inside the application directory...sometimes in a sub directory but most if not all of them are actually sitting in the directory I'm running wine in.

Here's  sample from 3dsmax.exe:
```
err:module:import_dll Library gup.dll (which is needed by L"E:\\3dsmax7\\3dsmax.exe") not found
err:module:import_dll Library AcGe16.dll (which is needed by L"E:\\3dsmax7\\core.dll") not found
err:module:import_dll Library core.dll (which is needed by L"E:\\3dsmax7\\bmm.dll") not found
err:module:import_dll Library bmm.dll (which is needed by L"E:\\3dsmax7\\imageViewers.dll") not found
err:module:import_dll Library AcGe16.dll (which is needed by L"E:\\3dsmax7\\core.dll") not found
err:module:import_dll Library core.dll (which is needed by L"E:\\3dsmax7\\imageViewers.dll") not found
err:module:import_dll Library imageViewers.dll (which is needed by L"E:\\3dsmax7\\3dsmax.exe") not found
err:module:import_dll Library AcGe16.dll (which is needed by L"E:\\3dsmax7\\core.dll") not found
err:module:import_dll Library core.dll (which is needed by L"E:\\3dsmax7\\menus.dll") not found
err:module:import_dll Library menus.dll (which is needed by L"E:\\3dsmax7\\3dsmax.exe") not found
err:module:import_dll Library AcGe16.dll (which is needed by L"E:\\3dsmax7\\core.dll") not found
err:module:import_dll Library core.dll (which is needed by L"E:\\3dsmax7\\bmm.dll") not found
err:module:import_dll Library bmm.dll (which is needed by L"E:\\3dsmax7\\viewfile.dll") not found
err:module:import_dll Library viewfile.dll (which is needed by L"E:\\3dsmax7\\3dsmax.exe") not found
```

That's some of the last lines.  It spits out many of these....just scrolls on and on.  Lots of the same libraries repeated, but not necessarily repeated.

I'm running "wine 3dsmax.exe" or "wine ./3dsmax.exe" in the 3dsmax directory.  There are only read privileges on the drive, but I shouldn't think that would cause a problem.  Not those kind of errors anyway.  I have wine 0.9.1 installed.

---

### Post by claydoh on 2005-11-21
If you are running the latest wine beta, have you run winecfg and set up your drives? I have found that it only sets up a fake c: drive, and your linux root ("/"). If you are running the installer on another partition not set up, it doesn't work. Also setting the D: drive to point to a cdrom helps as well. or copying the installer files to your home directory.

Browsing around didn't show much promise running 3dsmax in wine, though maya has a linux version.

---

