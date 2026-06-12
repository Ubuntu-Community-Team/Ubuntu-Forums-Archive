---
title: "MATLAB R2007a through Wine Problem"
date: 2010-01-22
forum: Education &amp; Science
---

### Post by macsdev on 2010-01-22
Hi,

I am trying to install MATLAB R2007a using Wine in my Ubuntu (Karmic Koala). The Installation happens properly but I get an error in the end saying some OLE server initialization problem. If I say Ok, it goes away and the installation completes successfully. If I open MATLAB, windows command window comes up for a second and says "Syntax Error, File not found" and closes immediately.

If I try to open MATLAB using terminal using "wine Matlab", I get a long list of errors like the following :
```

err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library mcr.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\matlab.exe") not found
err:module:import_dll Library libut.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\matlab.exe") not found
err:module:import_dll Library m_dispatcher.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\matlab.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\matlab.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\matlab.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\MATLAB\\R2007a\\bin\\win32\\matlab.exe" failed, status c0000135

```I saw somewhere that this error is due to the absence of Visual C++ runtime and installed that also through Wine. But, still I'm getting the error. Any help?

---

### Post by bondmatt on 2010-01-22
Do you need Simulink or some other graphical component of Matlab?
 
Best regards,
- Matt Bondy

---

### Post by vinke on 2010-01-23
Im sure you can run matlab nativly under Linux too.

---

### Post by earlycj5 on 2010-01-23
> **vinke said:**
> Im sure you can run matlab nativly under Linux too.

Yep, another post-doc in my lab uses Matlab whereas I use R, both with Linux.

---

### Post by nmaster on 2010-01-23
i use matlab for linux.  its great.  no bugs... but the linux/unix install disc is seperate from the windows one. it seems like the OP doesn't have this disc.

---

### Post by macsdev on 2010-01-23
@bondmatt

No, I don't need Simulink, atleast as of now.

@neal.m.master

In the disc I have, there is no linux version. Just the windows one.

Any solutions?

---

### Post by nmaster on 2010-01-23
you could try something like octave as a substitute.  i'd say just suck it up and buy the linux version.

---

### Post by macsdev on 2010-01-23
I am currently using Octave. But for large number crunching, octave seems slower. :(

---

### Post by meborc on 2010-01-24
i use matlab r2009b linux native and no problems... i suggest you check your university/division website... our university has a site where students can download and obtain matlab cd/license 

this is of course only for our university students and aquires a login/password to access

---

