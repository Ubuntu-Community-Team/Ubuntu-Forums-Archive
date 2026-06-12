---
title: "Wine, Matlab and .NET Framework"
date: 2008-07-25
forum: Education &amp; Science
---

### Post by Eredeath on 2008-07-25
I have MATLAB R2007a and am trying to make a complete switch to Linux from Vista. I've installed it under Wine and am coming up with one BIG error that I'm hoping someone knows a work-around.
In order to work MATLAB says it needs ".NET Framework installed before (I) can install the MATLAB builder for .NET".

any ideas (I'm assuming there is nothing i can do...)?

thanks in advance

---

### Post by chris200x9 on 2008-07-25
there is, I don't know how off hand but you could try googleing wine and .net sorry I couldn't be more help [http://appdb.winehq.org/appview.php?iVersionId=3754](http://appdb.winehq.org/appview.php?iVersionId=3754) so it can be done. I just don't know how, maybe download the exe from microsoft.com and run it under wine?

---

### Post by Sef on 2008-07-25
Moved to Education and Science.

---

### Post by Eredeath on 2008-07-25
Update: 

I've looked online and found a program called "mono" and i installed the windows version under wine hoping that will work but i still get the same error... the program really seems to want .NET 2.2 to work...

---

### Post by WW on 2008-07-26
You may already know this, but MATLAB has a Linux version.

---

### Post by Eredeath on 2008-07-26
i do know this, but i don't own that version of it :(

---

### Post by AnonCat on 2008-07-26
Paste the following into the terminal and see if it works:

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) && sh winetricks msxml3 dotnet20

---

### Post by Eredeath on 2008-07-26
Thank you, i am one step closer... to install what you gave me requires internet explorer 5.0.1 and i've tried to dwld that but it keeps quitting out because it cannot connect to the internet for some reason...
i think i'm going to try re-installing wine and seeing if that might fix it

---

### Post by Eredeath on 2008-07-26
okay, i did a fresh install of wine, and was able to successfully load those libraries (thx AnonCat) and MATLAB installs, but wont run. These are the errors I'm getting:
```
eredeath@EreDeath-Linux:~/.winetrickscache$ wine "C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\MATLAB.exe"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.ATL"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\uiw.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library ATL80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library comcli.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mcr.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.ATL"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.ATL"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\uiw.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library ATL80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library comcli.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mwoles05.DLL") not found
err:module:import_dll Library ATL80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mwoles05.DLL") not found
err:module:import_dll Library mwoles05.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mcr.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mlautoregister.dll") not found
err:module:import_dll Library mlautoregister.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mcr.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\uiw.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\hg.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\hg.dll") not found
err:module:import_dll Library hg.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mcr.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\uiw.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library mcr.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\MATLAB.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\MATLAB.exe" failed, status c0000135

```
any ideas how to get these libraries to work?

---

