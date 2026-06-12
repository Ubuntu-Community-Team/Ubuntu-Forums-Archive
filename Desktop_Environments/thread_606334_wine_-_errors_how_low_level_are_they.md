---
title: "wine - errors how low level are they?"
date: 2007-11-07
forum: Desktop Environments
---

### Post by gonnoc on 2007-11-07
Hi, I've never used linux before and I'm trialling ubuntu and overall I'm really starting to like it but there is a window's app that I'll find it hard living without so I came to wine.

I'm having some trouble running a windows application (SAS) with ubuntu 7.04 wine 0.9.33.
XP is what the application is running happily in currently and XP is the version of 
windows I've selected in the wine config utility.

I Installed wine then ran wine to do an app setup. The app  setup "appeared" to work but the app is not. I got the following errors and I'm wondering how deep into the bowels of wine they go,  essentially whether there is some chance they can be sorted without going into the wine source code.

The setup  seemed to work fine and finish cleanly (app GUI) but
these fixme messages were in the terminal window

fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\SASMONO.FOT","SASMONO.TTF","c:\\windows\\system32\\"): stub

fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\SASMONOB.FOT","SASMONOB.TTF","c:\\windows\\system32\\"): stub

fixme: ole:SLTG_DoRefs fname = C:\NT\System32\stdole32.tlb#OLE
err:seh:setup_exception stack overflow 144 bytes in thread 001d eip 7edf26ad esp 009def70 stack 0x9df000-0x9e0000

When I try to start the app by wine app.exe the app splash screen appears and I get the following error in the terminal
err:seh:setup_exception stack overflow 0 bytes in thread 0014 eip 7b88967a esp 009df000 stack 0x9df000-0x9e0000

When I try to start the app by selecting from the "Applications>Wine>Programs" option I get a dialogue from the app saying a config file cant be found but the file is actually sitting in the correct wine drive and directory location.

SAS is a very widely used stats & data manipulation package (I have an old version I like)
and I'd love to get it running if possible.  I'm sure it would open up lots of OS 
alternatives for students and others too if I could manage this with an open source
translation layer like wine

Thanks in advance for any help with this

---

### Post by MrFSL on 2007-11-07
Looks like there hasn't been much success running this app in wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3410](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3410)

You could try a virtual machine like vmware.

---

### Post by TeaSwigger on 2007-11-08
WINE is doing one heck of a task, and as such is naturally complicated and dicey. Virtualization is rapidly developing into a very useful option lately; if you do have a licensed windows installation disc and if you have plenty of ram to spare (and only if you do) then it's worth looking into. 

If it'll work in WINE you may have to be patient and fuss with it. Some thoughts -

First make sure WINE is actually set up as well as possible. Install, run wineprefixcreate, run winecfg, try it with a few apps known to work ok in WINE, get the hang of it so you understand the drive mapping and some other options, make any tweaks. Obviously if everything's not right with WINE it's asking for trouble running anything.

Second, the version of Windows you select for emulation is not literal, only different. It does happen that a program which works better natively on Windows XP works best in WINE under NT or 98. There is no harm done in trying different settings to see which if any work best with a given program.

Third, it is possible to extend WINE with dlls from your licenced copy of Windows, which can make all the difference, and install some Windows features. Errors, by log or terminal, can help discern what may help.

Fourth, there may always be errors reported, it's the nature of the beast; question is, does it work ok in spite of them.

Fifth, installing the program. Best practice to install it via terminal in the directory of the installer. If from a CD, it may help to copy the CD to the hard drive as an ISO, mount it, and install from there.

Sixth, launching the program. Sometimes it's best to use 

```
wine "c:\Program Files\Data\Lal.exe"
```

for instance, or perhaps

```
env WINEPREFIX="/home/lord_of_my_castle/.wine" WINEDEBUG=-all wine "c:\Program Files\Macromedia\Dreamweaver 8\Dreamweaver.exe"
```

or perhaps

```
wine /home/lord_of_my_castle/.wine/drive_c/Program\ Files/Macromedia/Dreamweaver\ 8/Dreamweaver.exe
```

Or it may not matter :p . And launching the app with a file from say a file manager like Nautilus requires a script, if it'll work. If you don't want to bother, launch the program empty and open the file internally or use WINE's own file browser, launched with:

```
winefile
```

Hope some of that might help.

---

