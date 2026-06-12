---
title: "Wine - MSVCP60.DLL missing"
date: 2005-12-18
forum: Gaming &amp; Leisure
---

### Post by Prudentissimus on 2005-12-18
I'm trying to run CONQUERONLINE ( MMORPG GAME ) through Wine.


Wine /media/hdb1/Conquer.exe 


But it gives me that MSVCP60.dll is missing.


How can I fix htis.?

---

### Post by Evil Whisper on 2005-12-18
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)

there you go just download that then unzip it and put it in your ~/.wine/drive_c/windows/system 

folder.

Hope This Helps,
- Evil Whisper

---

### Post by Prudentissimus on 2005-12-18
i do not have /drive_c/ in my wine dir...

is there anything i should config wine???

---

### Post by Evil Whisper on 2005-12-18
What version of wine are you using?

try typing this in your console:

```

wine --version

```

What folders do you have in your wine directory?

You should have somthing like this:

```

dosdevices  drive_c  system.reg  userdef.reg  user.reg

```

---

### Post by Prudentissimus on 2005-12-18
is that the default configuration? ( i am away from my linux computer right now.)

I have the latest wine... (downloaded via ATP today.)

DO I need any 3rd party config tools?

---

### Post by Evil Whisper on 2005-12-18
**[SIZE="5"]Installing Wine 0.9.3[/SIZE]**

Edit your sources.list file by typing the following in your console:
```

sudo gedit /etc/apt/sources.list

```

Scroll to the bottom of the file and add this:
```

## Wine HQ Repository
deb http://wine.sourceforge.net/apt/ binary/

```

Save and close the file next type this in console:
```

sudo apt-get remove wine

```

After thats done type this in console:
```

sudo apt-get update

```

Next we are going to create the apt prefrences file:
```

sudo gedit /etc/apt/preferences

```

Add this to the file:
```

Package: wine
Pin: release l=WineHQ APT Repository
Pin-Priority: 1000

```
(I got this part from winehq's website.)

Save and close the file.

now type this in console:
```

sudo apt-get install wine

```

You should now get a message about the file could not be authenticated or somthing
just answer yes and it will install.

Next type in your console:
```

winecfg

```

The wine configuration program should open.
You'll see a message in the console saying somthing like:
Creating .wine directory...

The wine config app looks like this:

[IMG]http://img54.imageshack.us/img54/5348/winecfg1si.png[/IMG]

I circled the button your suppost to click then click apply and OK.

now drop the DLL in the directory I mentioned in the first post and you should be all set.

Hope This Helps,
- Evil Whisper

---

### Post by Prudentissimus on 2005-12-18
HELP...


> prudens@lin:~$ wine /media/hdb1/Youxi/conq/play.exe
wine: Unhandled exception (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x00401610).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:00401610 ESP:7fb3f7b4 EBP:7fb3f920 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:7fb3f8a4 EDX:7fe0faa0
 ESI:7fb3fb10 EDI:00000000
Stack dump:
0x7fb3f7b4:  7fb3fb10 00000000 004014e0 7c04be28
0x7fb3f7c4:  004255b0 00001520 00001520 00000000
0x7fb3f7d4:  00000000 00000000 00000006 7e81d185
0x7fb3f7e4:  0000000f 00000000 00000000 00000000
0x7fb3f7f4:  00000000 00000000 00425718 0000144c
0x7fb3f804:  0000144c 00000000 00010026 0000144c
0200: sel=1007 base=b7ef2000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x00401610 in play (+0x1610) (0x7fb3f920)
  2 0x00419f52 in play (+0x19f52) (0x7fb3f940)
  3 0x004190b4 in play (+0x190b4) (0x7fb3f9a0)
  4 0x004192bd in play (+0x192bd) (0x7fb3f9bc)
  5 0x7f94e727 WINPROC_wrapper+0x17 in user32 (0x7fb3f9e0)
  6 0x7f94f234 in user32 (+0x8f234) (0x7fb3fa1c)
  7 0x7f952874 CallWindowProcA+0x7b in user32 (0x7fb3fa60)
  8 0x7f91fdab DispatchMessageA+0x152 in user32 (0x7fb3fa94)
  9 0x00417f1a in play (+0x17f1a) (0x0042f060)
  10 0x0000000f (0x00010026)
  11 0x00000000 (0x00000000)
0x00401610: movl        0x4(%edi),%edx
Modules:
Module  Address                 Debug info      Name (81 modules)
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e497000-7e4f9000     Deferred        libgnutls.so.11
ELF     0x7e4f9000-7e516000     Deferred        libcups.so.2
ELF     0x7e524000-7e570000     Deferred        libgcrypt.so.11
ELF     0x7e570000-7e580000     Deferred        libtasn1.so.2
ELF     0x7e5bb000-7e5d0000     Deferred        midimap<elf>
  \-PE  0x7e5c0000-7e5d0000     \               midimap
ELF     0x7e6ee000-7e711000     Deferred        msacm32<elf>
  \-PE  0x7e700000-7e711000     \               msacm32
ELF     0x7e711000-7e72a000     Deferred        msacm.drv<elf>
  \-PE  0x7e720000-7e72a000     \               msacm.drv
ELF     0x7e72a000-7e76d000     Deferred        wineoss.drv<elf>
  \-PE  0x7e740000-7e76d000     \               wineoss.drv
ELF     0x7e78b000-7e794000     Deferred        libxcursor.so.1
ELF     0x7e79f000-7e7bc000     Deferred        imm32<elf>
  \-PE  0x7e7b0000-7e7bc000     \               imm32
ELF     0x7e7bc000-7e7d8000     Deferred        ximcp.so.2
ELF     0x7e7d8000-7e7db000     Deferred        libxrandr.so.2
ELF     0x7e7db000-7e7e3000     Deferred        libxrender.so.1
ELF     0x7e7e3000-7e8a3000     Deferred        libx11.so.6
ELF     0x7e8a3000-7e8b0000     Deferred        libxext.so.6
ELF     0x7e8b0000-7e8c9000     Deferred        libice.so.6
ELF     0x7e8c9000-7e94b000     Deferred        winex11.drv<elf>
  \-PE  0x7e8e0000-7e94b000     \               winex11.drv
ELF     0x7e94b000-7e96a000     Deferred        libexpat.so.1
ELF     0x7e96a000-7e998000     Deferred        libfontconfig.so.1
ELF     0x7e998000-7e9ac000     Deferred        libz.so.1
ELF     0x7e9ac000-7ea16000     Deferred        libfreetype.so.6
ELF     0x7ea16000-7eaab000     Deferred        oleaut32<elf>
  \-PE  0x7ea30000-7eaab000     \               oleaut32
ELF     0x7eaab000-7eabf000     Deferred        olepro32<elf>
  \-PE  0x7eab0000-7eabf000     \               olepro32
ELF     0x7eabf000-7ead9000     Deferred        oledlg<elf>
  \-PE  0x7ead0000-7ead9000     \               oledlg
ELF     0x7ead9000-7eb04000     Deferred        winspool.drv<elf>
  \-PE  0x7eae0000-7eb04000     \               winspool.drv
ELF     0x7eb04000-7ebc3000     Deferred        comctl32<elf>
  \-PE  0x7eb10000-7ebc3000     \               comctl32
ELF     0x7ebc3000-7ebe4000     Deferred        iphlpapi<elf>
  \-PE  0x7ebd0000-7ebe4000     \               iphlpapi
ELF     0x7ebe4000-7ec2e000     Deferred        rpcrt4<elf>
  \-PE  0x7ec00000-7ec2e000     \               rpcrt4
ELF     0x7ec2e000-7ecb8000     Deferred        ole32<elf>
  \-PE  0x7ec50000-7ecb8000     \               ole32
ELF     0x7ecb8000-7ed14000     Deferred        shlwapi<elf>
  \-PE  0x7ecd0000-7ed14000     \               shlwapi
ELF     0x7ed14000-7edda000     Deferred        shell32<elf>
  \-PE  0x7ed30000-7edda000     \               shell32
ELF     0x7edda000-7ee6a000     Deferred        comdlg32<elf>
  \-PE  0x7edf0000-7ee6a000     \               comdlg32
ELF     0x7ee6a000-7eeab000     Deferred        advapi32<elf>
  \-PE  0x7ee80000-7eeab000     \               advapi32
ELF     0x7ef91000-7f894000     Deferred        gdi32<elf>
  \-PE  0x7efe0000-7f894000     \               gdi32
ELF     0x7f894000-7f9c0000     Export          user32<elf>
  \-PE  0x7f8c0000-7f9c0000     \               user32
ELF     0x7f9c0000-7fa40000     Deferred        winmm<elf>
  \-PE  0x7f9d0000-7fa40000     \               winmm
ELF     0x7fb42000-7fb46000     Deferred        libxdmcp.so.6
ELF     0x7fb46000-7fb49000     Deferred        libxau.so.6
ELF     0x7fb49000-7fb50000     Deferred        libsm.so.6
ELF     0x7fb52000-7fb5d000     Deferred        libgcc_s.so.1
ELF     0x7fca5000-7fdb0000     Deferred        kernel32<elf>
  \-PE  0x7fcd0000-7fdb0000     \               kernel32
ELF     0x7fec1000-7fecb000     Deferred        libnss_files.so.2
ELF     0x7fecb000-7fed4000     Deferred        libnss_nis.so.2
ELF     0x7fed4000-7fee9000     Deferred        libnsl.so.1
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7d81000-b7d85000     Deferred        libgpg-error.so.0
ELF     0xb7d85000-b7d89000     Deferred        libxfixes.so.3
ELF     0xb7d89000-b7d8b000     Deferred        xlcutf8load.so.2
ELF     0xb7d8d000-b7d90000     Deferred        libdl.so.2
ELF     0xb7d90000-b7ebe000     Deferred        libc.so.6
ELF     0xb7ebe000-b7ed0000     Deferred        libpthread.so.0
ELF     0xb7ed0000-b7ee9000     Deferred        libwine.so.1
ELF     0xb7ee9000-b7ef2000     Deferred        libnss_compat.so.2
ELF     0xb7ef7000-b7f0d000     Deferred        ld-linux.so.2
PE      0x00400000-00442000     Export          play
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) F:\Youxi\conq\play.exe
        00000009    0 <==
WineDbg terminated on pid 0x8
wine client error:9: write: Bad file descriptor


---

### Post by Prudentissimus on 2005-12-18
how do you change from 32 to 16 bit display?

---

### Post by Evil Whisper on 2005-12-18
what wine version?  If its older then 0.9.3 install wine 0.9.3.

It appears that the game you are trying to run uses Direct X and wine 0.9.3 is the only version I've ever been able to get Direct X things to run on.

Not quite sure about the 16 bit thing.

---

### Post by Prudentissimus on 2005-12-18
how do you change the display color depth from 32 to 16/??

---

### Post by Evil Whisper on 2005-12-18
I think the option to that is in your xorg.conf file thats all I could find from googling but I never touch that file because every time I do I break my X server lol :(

[http://www.google.com/linux?q=xorg+16bit+color+mode](http://www.google.com/linux?q=xorg+16bit+color+mode)

one of the pages there says you have to find this line:

```

DefaultDepth	24

```

and change it to
```

DefaultDepth	16

```

**If your going to try this please back up your xorg.conf file!**

---

### Post by Prudentissimus on 2005-12-18
there's a thing I can modify in Winecfg, in graphics tab...

but seems doesn't do the trick...

> prudens@lin:/media/hdb1/Youxi/conq$ wine play.exe
prudens@lin:/media/hdb1/Youxi/conq$ fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DImpl_CreateDevice (0x7ba997d8) Incomplete stub for d3d8
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  4619
  Current serial number in output stream:  4619


---

### Post by Evil Whisper on 2005-12-18
I think instead of editing your xorg.conf file you might be able to hit control+alt+backspace and type this at the prompt:

```

startx --bpp 16

```

---

### Post by Prudentissimus on 2005-12-18
OK I think I got through that display problem...

Now here's what I get
> prudens@lin:/media/hdb1/Youxi/conq$ fixme:d3d:IWineD3DImpl_CreateDevice (0x7ba67f10) Incomplete stub for d3d8
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  4615
  Current serial number in output stream:  4615



Which version of Wine did you say I should download??? Where can I get it? Mine is the 20050725 version

---

### Post by Evil Whisper on 2005-12-18
Wine 0.9.3 is the version you should use.

I posted a how-to for installing it here:

[http://www.ubuntuforums.org/showthread.php?p=586605#post586605](http://www.ubuntuforums.org/showthread.php?p=586605#post586605)

---

### Post by Prudentissimus on 2005-12-18
do i have to uninstall the current?

---

### Post by Evil Whisper on 2005-12-18
Yes, it would be a good idea to uninstall the current.

---

### Post by Prudentissimus on 2005-12-18
still

> prudens@lin:/media/hdb1/Youxi/conq$ wine play.exe
prudens@lin:/media/hdb1/Youxi/conq$ fixme:d3d:IWineD3DImpl_CreateDevice (0x7bb8c5a8) Incomplete stub for d3d8
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  389
  Current serial number in output stream:  389



---

### Post by Evil Whisper on 2005-12-18
Well you could try downloading this DLL:

[http://www.dll-files.com/dllindex/dll-files.shtml?dinput](http://www.dll-files.com/dllindex/dll-files.shtml?dinput)

and putting it in the same folder as you put the first missing dll in.

then run winecfg and add:

```

dinput.dll

```

into the new dll override for library box on the Libraries tab and then click add.
I found this little bit of info on winehq.

(Slightly Offtopic: how much does this game cost?  If its free I'll download it and mess with it and see if I can get it working.)

**If you have MSN messenger and would like to talk about this in real time PM me your MSN**

---

### Post by Prudentissimus on 2005-12-18
the game is free

[http://www.conqueronline.com](http://www.conqueronline.com)

I am Prudens on Phoenix server.

I am lvl 98 archer.


My MSN is [email]PrudensOptimum@hotmail.com[/email]

---

### Post by Evil Whisper on 2005-12-19
Cool i'll download it today.

I've added you to msn.

---

### Post by guatebus on 2009-04-16
I needed the same library for another application (TypeFaster) so I downloaded from here:

[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)

Unzipped it, changed the name from MSVCP60.DLL to msvcp60.dll and copied it into the 

/windows/system   

and   

/windows/system32 

folders of wine installations of all users. The location of /system and /system32 folders:
 
~/c/windows/system 
~/c/windows/system32  

~/.wine/drive_c/windows/system 
~/.wine/drive_c/windows/system32

It worked for me... finally! :D  hope it helps!

---

