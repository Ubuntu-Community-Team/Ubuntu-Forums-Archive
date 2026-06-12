---
title: "using wine?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by Vlatko on 2006-07-29
ok so i succesfully(i think) installed wine on my amd64 ubuntu machine using this guide. [http://www.ubuntuforums.org/showthread.php?t=185557&page=8](http://www.ubuntuforums.org/showthread.php?t=185557&page=8)

so far i managed to open winecfg and that's about it. :D what's next? how do i open windows programs?

thanks!

---

### Post by Lord Illidan on 2006-07-29
Well...try downloading the p2p program named ares, for example.

Download it in a specific directory, say, ~/software

The ~ is a symbol for your home directory, ok?

Then go to a terminal, and type

```
wine /home/vlatko/software/aresregular192_installer.exe
```

---

### Post by Vlatko on 2006-07-29
> **Lord Illidan said:**
> Well...try downloading the p2p program named ares, for example.

Download it in a specific directory, say, ~/software

The ~ is a symbol for your home directory, ok?

Then go to a terminal, and type

```
wine /home/vlatko/software/aresregular192_installer.exe
```
aha...i thought i could use programmes already installed on the windows partition. silly me. :D  (complete noob)

---

### Post by Lord Illidan on 2006-07-29
> **Vlatko said:**
> aha...i thought i could use programmes already installed on the windows partition. silly me. :D  (complete noob)

You can... copy their folders to ~/.wine/drive_c/

And run them from there. Not everything may work. If you tell us what programmes you want to run, we can give you specific tips.

---

### Post by Vlatko on 2006-07-29
> **Lord Illidan said:**
> You can... copy their folders to ~/.wine/drive_c/

And run them from there. Not everything may work. If you tell us what programmes you want to run, we can give you specific tips.
well i'd like to try winamp. problem is i can't find that ".wine" directory. i have a "c" directory on my home partition, it contains two folders windows and program files. is that the same? so i just copy the winamp folder to there and run it like this 

> vlatko@vlatko-desktop:~$ wine /home/vlatko/c/winamp/winamp.exe

edit: it worked! winamp opened and i could play it! ok so that's how. i did get these errors in the terminal though.

```
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\winamp\\Plugins\\Evil.dll") not found
fixme:powrprof:DllMain (0x58250000, 1, (nil)) not fully implemented
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
fixme:shell:SHAppBarMessage ABM_REMOVE broken
fixme:powrprof:DllMain (0x58250000, 0, (nil)) not fully implemented
```

any ideas how to resolve it?

thanks a lot btw ;)

---

### Post by Vlatko on 2006-07-29
> err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\winamp\\Plugins\\Evil.dll") not found
i think this line of the error message is caused cause winamp starts with a program "evil lyrics" which is unavailable in wine. obviously. :)

---

### Post by Vlatko on 2006-07-29
ok this maybe too much all at once but i am eager to get this thing working. :D so i copied the internet explorer folder to the c drive and started it and i got a bunch of errors. a window did open but it was completely blank, only the title name said "WINE INTERNET EXPLORER"

here are the error messages i got:
```
vlatko@vlatko-desktop:~$ wine /home/vlatko/c/ie/iexplore.exe
fixme:shdocvw:IEWinMain "" 1
fixme:ole:CoResumeClassObjects stub
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x5591b5ec)->((null) 1 0x55c2fb0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x5591b5ec)->((null) 25 0 0x55c2fb20 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x5591b5ec)->((null) 26 0 0x55c2fb20 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x5591b5ec)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x55c2fa74 0x55c2fac0 (nil) 0x55c2fa84)
fixme:shdocvw:ClDispatch_Invoke (0x5591b5ec)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x55c2fa34 0x55c2fa80 (nil) 0x55c2fa44)
fixme:shdocvw:ClDispatch_Invoke (0x5591b5ec)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x55c2fa74 0x55c2fac0 (nil) 0x55c2fa84)
fixme:shdocvw:ClDispatch_Invoke (0x5591b5ec)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x55c2fa34 0x55c2fa80 (nil) 0x55c2fa44)
fixme:shdocvw:ClDispatch_Invoke (0x5591b5ec)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x55c2fa74 0x55c2fac0 (nil) 0x55c2fa84)
fixme:shdocvw:ClDispatch_Invoke (0x5591b5ec)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x55c2fa74 0x55c2fac0 (nil) 0x55c2fa84)
fixme:shdocvw:ClDispatch_Invoke (0x5591b5ec)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x55c2fa74 0x55c2fac0 (nil) 0x55c2fa84)
fixme:shdocvw:ClientSite_GetContainer (0x5591b5ec)->(0x55c2fb4c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x5591b5ec)->({000214d1-0000-0000-c000-000000000046} 37 0 0x55c2fc50 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x5591cd90)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x5591cec8)
vlatko@vlatko-desktop:~$
```

---

### Post by Vlatko on 2006-07-29
no ideas? i really internet explorer to work. :)

---

### Post by piercy on 2006-07-29
erm i would just use firefox instead of internet explorer to be honest. its a bit of a wste of time copying IE over.  you will have a much more stable browser if you stick with firefox. i only use win for aps i cant get on linux.  for instance xfire and teamspeak although neither of them worked very well.

---

### Post by Vlatko on 2006-07-29
> **piercy said:**
> erm i would just use firefox instead of internet explorer to be honest. its a bit of a wste of time copying IE over.  you will have a much more stable browser if you stick with firefox. i only use win for aps i cant get on linux.  for instance xfire and teamspeak although neither of them worked very well.
i do use firefox(and opera) but some sites i use frequently are ie only so i would need internet explorer to be able to run on ubuntu. :(

---

### Post by Vlatko on 2006-07-29
ok i am also having trouble running wine tools. this is the error i get

```
vlatko@vlatko-desktop:~$ wt
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0.9.17
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.17".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/vlatko/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

i checked synaptic, libgtk-1.2.so.0 is installed. i don't know what's the problem.:(

---

### Post by elizleisndahizle on 2006-08-10
there is a great firefox extension that lets you change a setting so the website that you are visiting thinks you are using a different browser like IE.  Which can be found here [https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/) another idea is to use you're winamp settings with xmms.  I was thinking that it was called Amp at one time and was later ported over to windows and called winamp but i might be wrong.

---

### Post by Billquinn1 on 2006-08-10
Ok, this is a pain but it will work. First you will need to remove the wine installation you already have. Use synaptic and to remove wine, then delete the ./wine folder. Then follow this guys guide:

[HTML]http://doc.gwos.org/index.php/WineSetup[/HTML]

The version of wine is critical to getting IE to work. I hate IE myself but there are times you just can't avoid it. 
After you get IE to work DO NOT UPGRADE WINE. For some reason this version of wine is very stable for IE. Then go into synaptic and "lock version".

Good Luck.

---

