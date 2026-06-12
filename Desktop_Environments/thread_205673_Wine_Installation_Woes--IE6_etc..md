---
title: "Wine Installation Woes--IE6 etc."
date: 2006-06-28
forum: Desktop Environments
---

### Post by Mike-97470 on 2006-06-28
I installed Wine 0.9.5 in accordance with the following "HOWTO Setup Wine" thread--http://www.ubuntuforums.org/showthread.php?t=149585

I then installed winetools 0.9, used it to setup a c: drive, etc., and installed IE6.  IE seemed to work, at least I was able to visit my only IE specific website.  But after installing the rest of the M$ stuff, IE stopped working.  (I've also tried wine 0.9.9 and 0.9.16, but that's another story--I've also tried installing a couple of my Windows only aps and they don't work either.)

Here's the Terminal output when I run IE:
(The IE window pops up, but it hangs without getting to the msn website or whatever)
=======================================================
mike@MikesPavillion:~$ wine "/home/mike/.wine/drive_c/Program Files/Internet Explorer/IEXPLORE.EXE"
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:actctx:ActivateActCtx stub!
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
.
.
.
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:toolbar:TOOLBAR_CheckStyle [0x10032] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10032] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10032,0x00008003,0x00008000,0x0000c071,0x00000001,0x7fbbd928):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10032, wParam=0x00000000, size.cx=1024, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10032] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10032] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_SetExtendedStyle Unknown Toolbar Extended Style 0x00000080. Please report.
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x10038 wParam 00000001 lParam 00000000
fixme:toolbar:TOOLBAR_SetExtendedStyle Unknown Toolbar Extended Style 0x00000080. Please report.
fixme:advapi:CheckTokenMembership ((nil) 0x7fd60008 0x7fbbd79c) stub!
fixme:dpa:DPA_LoadStream phDpa=0x7fbbd364 loadProc=0x7117ba1c pStream=0x7fd5efa0 lParam=7fd66ad8
fixme:dpa:DPA_LoadStream dwSize=0 dwData2=0 dwItems=0
fixme:dpa:DPA_LoadStream new hDpa=0x7fd66b70, errorcode=80004005
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10052, wParam=0x00000000, size.cx=1024, size.cy=764 stub!
fixme:shell:NTSHChangeNotifyRegister (0x10052,0x00008003,0x0c02b7ff,0x0000c071,0x00000001,0x7fbbd968):semi stub.
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
fixme:actctx:CreateActCtxW stub!
fixme:thread:QueueUserWorkItem (0x70c1a6f2,0x7fd780a8,0x00000000): stub
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
fixme:shell:NTSHChangeNotifyRegister (0x10026,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x7fbbeaa0):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:win:GetProcessDefaultLayout ( 0x7fbbeab4 ): No BiDi
fixme:win:GetProcessDefaultLayout ( 0x7fbbeab4 ): No BiDi
fixme:shell:SHFlushClipboard stub
fixme:shell:DllCanUnloadNow stub
fixme:actctx:DeactivateActCtx stub!
fixme:shell:DllCanUnloadNow stub
mike@MikesPavillion:~$
=======================================================
Here's the winetools.log
Winetools 0.9 configuration = installed at 28.06.2006 14:49:47
*new* fake Windows drive = installed at 28.06.2006 14:49:48
arial32.exe = installed at 28.06.2006 14:50:09
dcom98.exe = installed at 28.06.2006 14:50:28
mfc40.dll = installed at 28.06.2006 14:50:39
mfc42.dll = installed at 28.06.2006 14:50:45
Microsoft Internet Explorer.* = installed at 28.06.2006 14:52:10
Msvbvm50.exe = installed at 28.06.2006 14:54:35
vbrun60sp5.exe = installed at 28.06.2006 14:55:00
vc6redistsetup_enu.exe = installed at 28.06.2006 14:55:27
vcredist.exe = installed at 28.06.2006 14:55:47
MDAC_TYP.EXE = installed at 28.06.2006 14:57:48
Jet40SP8_9xNT.exe = installed at 28.06.2006 14:58:26
MDAC_TYP.EXE = installed at 28.06.2006 15:01:18
msxml.msi = installed at 28.06.2006 15:02:21
scr56en.exe = installed at 28.06.2006 15:03:03
50comupd.exe = installed at 28.06.2006 15:03:47
-----------------------------
Any help is much appreciated!

---

### Post by littlespy on 2006-06-28
im not sure but it looks like you've installed a lot of libraries that wine might not be able to to handle, your best bet would probably be to reinstall wine and start over

---

### Post by Scunizi on 2006-06-28
If you have a valid copy of Windows, take a look at Qemu in Synaptic.  With that you should be able to load the entire windows system including IE.  I'm still playing with it but haven't had any time in the last 2 weeks to even try.  I did manage to get W2kpro loaded with some quirks.  There are lots of people that are having success there.  Unfortunatly, some things still don't work.  I need specific work related websites under IE, my scanning and faxing software that I haven't been able to duplicate in Ubuntu as yet.

---

### Post by jimmygoon on 2006-06-28
You really ought to just use this: [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html) (just install wine and run this package). I've successfully used it to install IE6, Fonts, Windows Media Player etc etc

A couple of suggestions:
Either use the lastest CVS from the Wine Repos or at least download the lastest stable version from the wine Repos because both will be newer and better than Ubuntus. normally I wouldn't say that but I couldn't the that package working with Ubuntu's version, but I could with the lastest stable wine version. (of course that was months ago... it could've changed by now I suppose.

---

