---
title: "Run PSPICE in Wine"
date: 2007-09-14
forum: Education &amp; Science
---

### Post by burnttoast11 on 2007-09-14
Hey, I am pretty new to Ubuntu and just got Wine.  I was wondering if anyone has got PSPICE 9.1 working under Wine.  Here is how far I have gotten with it.

1) Installed it without a problem.

2) Tried running PSpice Schematics but no parts were found so I couldn't build a circuit.  I got an error message about an .ini file.  I copied "C:\WINDOWS\PSPICEEV.INI" from a Windows XP installation of PSPICE onto my Ubuntu computer.

3) Now PSpice finds the parts and I can build a circuit, however when I tried to simulate the circuit I get the following error. 

"Exception Calling SimServer loadProfile"

Anyone have any suggestions?

Peder

---

### Post by xeniter on 2007-09-27
i have the same problems

have anyone some ideas??

mfg xeniter

if you have a solution please mail it to me: [email]xeniter@hotmail.com[/email]

when i have one, i will tell you

---

### Post by slimdog360 on 2007-09-28
you may want to give ngspice a try [http://ngspice.sourceforge.net/]("http://ngspice.sourceforge.net/").

I gave pspice a go under wine a while back and it didn't work completely correctly for me either. You may be able to use something like [virtualbox]("http://www.virtualbox.org/") and run pspice under windows with this.

---

### Post by burnttoast11 on 2007-10-26
I did some googling and found something that I thought might help.  I found this at the Orcad website.

Windows registry error, "Can't connect to Simulation Server (simsrvr)" when attemping to simulate


```
PROBLEM:
How do I solve a Windows registry problem ("Can't connect to Simulation Server (simsrvr)" message) when attemping to simulate?

SOLUTION:
Type in the following commands from the MS-DOS prompt. Windows_dir is your installed Windows directory. OrCAD_dir is your installed OrCAD v9.0 directory.

   1. cd windows_dir\system regsvr32 atl.dll
   2. cd orcad_dir\capture regsvr32 pipspice.dll
   3. cd orcad_dir\pspice pspice /regserver simsrvr /regserver mrksrvr /regserver
   4. If this fails, re-install DCOM95, then redo steps 1 and 2.

To install DCOM95, run setup in the DCOM directory on the OrCAD v9.0 CD-ROM. NOTE: Re-installing the OrCAD 9 software will also correct registry problems.
```

So I opened cmd.exe in WINE and tried those steps.  Step one works fine.  But when I try to do step 2, I get the following error.

```
C:\Program Files\OrCAD_Demo\Capture>regsvr32 PipSpice.dll
fixme:atl:AtlModuleInit SEMI-STUB (0x1002feb0 0x1002f7c0 0x10000000)
Failed to register DLL PipSpice.dll
wine: Unhandled page fault on read access to 0x73616942 at address 0x73616942 (thread 000d), starting debugger...
Unhandled exception: page fault on read access to 0x73616942 in 32-bit code (0x73616942).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:73616942 ESP:0034fd5c EBP:0034fd88 EFLAGS:00010202(   - 00      - -RI1)
 EAX:756c6156 EBX:7c384e68 ECX:0034fdb0 EDX:10025990
 ESI:0012d080 EDI:00000000
Stack dump:
0x0034fd5c:  7c37b7ba 756c6156 0012bee8 0034fd7c
0x0034fd6c:  5f4777cd 5f40faef 0012bee8 7c37b78b
0x0034fd7c:  10000000 1002fd58 00000000 0034fdbc
0x0034fd8c:  1001302f 1002feb0 00000001 0034fdb8
0x0034fd9c:  7c6a6c42 1002fd58 0034fdd8 5f401018
0x0034fdac:  10012f91 0034fdcc 10022ac8 ffffffff
Backtrace:
=>1 0x73616942 (0x0034fd88)
fixme:dbghelp_msc:pe_load_debug_directory This guy has FPO information
  2 0x1001302f in pipspice (+0x1302f) (0x0034fdbc)
  3 0x10020235 in pipspice (+0x20235) (0x0034fdd8)
  4 0x10020586 in pipspice (+0x20586) (0x0034fe18)
  5 0x7bc4392d in ntdll (+0x3392d) (0x0034fea8)
  6 0x7bc43d6f in ntdll (+0x33d6f) (0x0034fec8)
  7 0x7b87228f ExitProcess+0x1f() in kernel32 (0x0034fee8)
  8 0x7ee7872a in regsvr32 (+0x872a) (0x0034ff08)
  9 0x7b874dfe in kernel32 (+0x54dfe) (0x0034ffe8)
  10 0xb7de19d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x73616942: -- no code accessible --
Modules:
Module  Address                 Debug info      Name (92 modules)
PE        460000-  499000       Deferred        psp_wobj
PE      10000000-1003e000       Export          pipspice
PE      14000000-141c0000       Deferred        db_dll
PE      5f400000-5f4f2000       Deferred        mfc42
PE      780c0000-7814d000       Deferred        msvcp50
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Export          ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bcf6000-7bd47000       Deferred        libgcrypt.so.11
ELF     7bd47000-7bd57000       Deferred        libtasn1.so.3
ELF     7bd57000-7bd85000       Deferred        libcrypt.so.1
ELF     7bd85000-7bdf5000       Deferred        libgnutls.so.13
ELF     7bdf5000-7be1a000       Deferred        libk5crypto.so.3
ELF     7be1a000-7bea2000       Deferred        libkrb5.so.3
ELF     7bea2000-7becb000       Deferred        libgssapi_krb5.so.2
ELF     7becb000-7bf00000       Deferred        libcups.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf30000-7bf62000       Deferred        uxtheme<elf>
  \-PE  7bf40000-7bf62000       \               uxtheme
ELF     7bf62000-7c000000       Deferred        oleaut32<elf>
  \-PE  7bf70000-7c000000       \               oleaut32
ELF     7c32d000-7c331000       Deferred        libgpg-error.so.0
ELF     7c331000-7c333000       Deferred        libkeyutils.so.1
ELF     7c333000-7c33b000       Deferred        libkrb5support.so.0
ELF     7c364000-7c386000       Deferred        atl<elf>
  \-PE  7c370000-7c386000       \               atl
ELF     7c386000-7c3bb000       Deferred        winspool<elf>
  \-PE  7c390000-7c3bb000       \               winspool
ELF     7c3bb000-7c479000       Deferred        comctl32<elf>
  \-PE  7c3c0000-7c479000       \               comctl32
ELF     7c479000-7c4d2000       Deferred        shlwapi<elf>
  \-PE  7c490000-7c4d2000       \               shlwapi
ELF     7c4d2000-7c5d5000       Deferred        shell32<elf>
  \-PE  7c4e0000-7c5d5000       \               shell32
ELF     7c5d5000-7c676000       Deferred        comdlg32<elf>
  \-PE  7c5e0000-7c676000       \               comdlg32
ELF     7c676000-7c6de000       Deferred        msvcrt<elf>
  \-PE  7c690000-7c6de000       \               msvcrt
ELF     7c6de000-7c6f2000       Deferred        lz32<elf>
  \-PE  7c6e0000-7c6f2000       \               lz32
ELF     7c6f2000-7c70c000       Deferred        version<elf>
  \-PE  7c700000-7c70c000       \               version
ELF     7c70c000-7c715000       Deferred        libxcursor.so.1
ELF     7c715000-7c732000       Deferred        imm32<elf>
  \-PE  7c720000-7c732000       \               imm32
ELF     7c732000-7c73a000       Deferred        libxrender.so.1
ELF     7e545000-7e78e000       Deferred        i915_dri.so
ELF     7e78e000-7e798000       Deferred        libdrm.so.2
ELF     7e798000-7e79d000       Deferred        libxfixes.so.3
ELF     7e79d000-7e7a0000       Deferred        libxdamage.so.1
ELF     7e7a0000-7e801000       Deferred        libgl.so.1
ELF     7e801000-7e806000       Deferred        libxdmcp.so.6
ELF     7e806000-7e8f7000       Deferred        libx11.so.6
ELF     7e8f7000-7e905000       Deferred        libxext.so.6
ELF     7e905000-7e90a000       Deferred        libxxf86vm.so.1
ELF     7e90a000-7e922000       Deferred        libice.so.6
ELF     7e922000-7e92a000       Deferred        libsm.so.6
ELF     7e92a000-7e92d000       Deferred        libcom_err.so.2
ELF     7e92f000-7e935000       Deferred        libxrandr.so.2
ELF     7e935000-7e9c1000       Deferred        winex11<elf>
  \-PE  7e940000-7e9c1000       \               winex11
ELF     7ea3e000-7ea5e000       Deferred        libexpat.so.1
ELF     7ea5e000-7ea89000       Deferred        libfontconfig.so.1
ELF     7ea94000-7eaa9000       Deferred        libz.so.1
ELF     7eaa9000-7eb19000       Deferred        libfreetype.so.6
ELF     7eb19000-7eb2c000       Deferred        libresolv.so.2
ELF     7eb2c000-7eb4a000       Deferred        iphlpapi<elf>
  \-PE  7eb30000-7eb4a000       \               iphlpapi
ELF     7eb4a000-7eba3000       Deferred        rpcrt4<elf>
  \-PE  7eb60000-7eba3000       \               rpcrt4
ELF     7eba3000-7ec3e000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec3e000       \               gdi32
ELF     7ec3e000-7ed7c000       Deferred        user32<elf>
  \-PE  7ec60000-7ed7c000       \               user32
ELF     7ed7c000-7edc5000       Deferred        advapi32<elf>
  \-PE  7ed90000-7edc5000       \               advapi32
ELF     7edc5000-7ee66000       Deferred        ole32<elf>
  \-PE  7edd0000-7ee66000       \               ole32
ELF     7ee66000-7ee7a000       Export          regsvr32<elf>
  \-PE  7ee70000-7ee7a000       \               regsvr32
ELF     7ee7a000-7ee85000       Deferred        libnss_files.so.2
ELF     7ee85000-7ee9d000       Deferred        libnsl.so.1
ELF     7ee9d000-7eea6000       Deferred        libnss_compat.so.2
ELF     7eea6000-7eea9000       Deferred        libxau.so.6
ELF     7efd0000-7eff5000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c68000-b7c6c000       Deferred        libdl.so.2
ELF     b7c6c000-b7db6000       Deferred        libc.so.6
ELF     b7db7000-b7dcf000       Deferred        libpthread.so.0
ELF     b7dda000-b7eee000       Export          libwine.so.1
ELF     b7ef0000-b7f0c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
        00000010    0
        0000000f    0
0000000c (D) c:\windows\system32\regsvr32.exe
        0000000d    0 <==
00000008 
        00000009    0

```

So I guess this must be the dll that is causing the problems.  Does anyone have any ideas?

---

### Post by villindesign on 2007-10-28
You guys should try [LTSpice]("http://www.linear.com/designtools/software/") made by Linear Technology. It is a win32 app, but the programmers promise that the releases will be compatible with wine. So, once you have wine installed, download and install LTSpice. It is also a great program and PSpice replacement.

---

### Post by mrfuzzemz on 2007-12-15
There is a temporary solution to the "Placing Parts" problem.  Hopefully it will be included with wine updates in the near future.

Here is a link to the bug:

[http://bugs.winehq.org/show_bug.cgi?id=3023](http://bugs.winehq.org/show_bug.cgi?id=3023)

Unfortunately it requires recompiling wine.  I will see what I can do about creating a modified deb package.

---

### Post by eldragon on 2007-12-15
its sad there is no good alternative to spice, or even orcad for linux.

i found it much more hassle free to install VirtualBox, and run a virtual XP just for the orcad suit. its a tad bit slow, but it works, and i will never dualboot again in my life :D

---

### Post by Jack-in-Box on 2008-07-31
I would just like to re-iterate Villindesign's suggestion to use LTSpice ([http://www.linear.com/designtools/software/switchercad.jsp](http://www.linear.com/designtools/software/switchercad.jsp)). I have been using it in the most demanding high frequency analogue design applications and found it the best Spice simulator I have used bar none .. as well as which, from my experience, it works straight out of the box with Wine on Ubuntu and Suse.. and is free! It has not been designed to integrate easily into an integrated design package like pSpice and Orcad, but, depending on what you are trying to do, that kind if integration can cause as many problems as it solves.

---

### Post by john.silver on 2008-10-11
Hi,
I have just made to work PSpice 9.2 under Wine 1.1.5, hooray :-)
I'm running Ubuntu 7.10 and I have tried to make it work many times, but under the old version of Wine.

Now I tried to install the new version, and it seems to be working. To be more specific what works - creating and saving schematics and SIMULATING of them!

As mentioned above, it is necessary to install Wine 1.1.5, then install PSpice, BUT I think it is better to install it to the directory named with no spaces (not to Program Files as default). Because when I tried recently to uninstall it, it said something about bad path 'C:\Program\', and aborted.

Next it is necessary to install DCOM98 via winetricks and make Wine emulating Windows 98. 
To make loading parts from library available, get a pspice.ini file from a working installation under real Windows, or download some from the internet and change Program Files to the path you have installed Pspice under Wine.
And everything works like a dream :-)

Hope you will be succesfull as I have been :-)

---

### Post by Psychey on 2008-11-12
Hello.

After a bit of fighting with Wine, I finally got pSpice 9.2 Student Version working with Wine 1.1.4. Here is how I did it:

* Started with a clean Wine cfg (deleted the ~/.wine folder)
* Installed pSpice
* Installed dcom98 via. winetricks:
  wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
  chmod 777 winetricks
  ./winetricks dcom98

* Copied the PSPICEEV.INI file from my an installation of pSpice I had on windows to my wine windows dir, so:
  cp <whatever path you may or may not have mounted you windows drive to>/Windows/PSPICEEV.INI ~/.wine/drive_c/windows/PSPICEEV.INI
  (this is in order to have pSpice find the library components.)
  Note that if you installed pSpice in a different location on your Wine-dir than on your Windows installation you must also edit that .ini file to match the correct path).

* (may not be necessary, but I had to do this)
  Run:
  winecfg
  ...and select "Windows 98" as "Windows version" under the "Applications tab". Then head over to the "Libraries tab", select the three different "overrides" (ole32, oleaut32, rpcrt4) in turn and click "Edit", and select "Native (Windows)" instead of the default "Native when builtin". If you do not have the three overrides listed, chances are that the dcom98 package was not installed correctly.

This solved it for me. I am now running pSpice through Wine, and have yet to encounter a problem with it.

I just got yet another reason not to start up my Windows installation. Suits me perfectly. :)

Have fun!

---

### Post by Rob_Frohne on 2009-07-21
I made it work with PSPICE 9.1 and wine 1.0.1 with Ubuntu Jaunty by doing the following:

1)  I installed it in a directory with no spaces in it.
2)  I followed the advice of the person above.  You need a PSPICEEV.INI that is known to work with the installed version on a Windows machine, and then edited with the appropriate path names.

I hope this helps someone else.  :)

Rob

---

### Post by neoraist on 2009-10-13
Works for me!

After all, I don't need an original windows ini file;

1) Install pspice without any spaces c:\orcad_demo
2) install dcom98 from wintricks
3) open schematics and  go to: Option - Editor cofiguration.

3.1) Write "C:\OrCAD_Demo\PSpice\Library"; in library path.
3.2) library settings ... and "add*" and "add local" all libraries from /.../pspice/library (for me, the program say that i can only add 10 local libraries, so I don't add the last one)

Go to get new part and there are all.
Simulate works to.


PS: I don't know the diference betwen "add*" and "add local"

---

### Post by rodrigor on 2010-04-07
> **Jack-in-Box said:**
> I would just like to re-iterate Villindesign's suggestion to use LTSpice ([http://www.linear.com/designtools/software/switchercad.jsp](http://www.linear.com/designtools/software/switchercad.jsp)). I have been using it in the most demanding high frequency analogue design applications and found it the best Spice simulator I have used bar none .. as well as which, from my experience, it works straight out of the box with Wine on Ubuntu and Suse.. and is free! It has not been designed to integrate easily into an integrated design package like pSpice and Orcad, but, depending on what you are trying to do, that kind if integration can cause as many problems as it solves.

i tried winetricks but after installing dcom98 wine failed to install pspice, i've spent enough time on gEDA, maybe if i started from 0 on my own it would work all right, but my university gave me pspice .cir files and i've lost enough time trying to make gnucap work.
linear's software worked fine on wine, on the first run.
thnks!

---

### Post by sdaau on 2010-09-08
Hi all, 

Just wanted to say - thanks for this thread, helped me to install PSpice 9.1 under Ubuntu 10.04; here are my steps: 

[[SOLVED] Installing & Running PSpice Student 9.1 on Ubuntu Lucid - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1570404)

Cheers!

---

