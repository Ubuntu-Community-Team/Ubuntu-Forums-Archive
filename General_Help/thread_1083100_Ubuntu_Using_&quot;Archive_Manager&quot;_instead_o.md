---
title: "Ubuntu Using &quot;Archive Manager&quot; instead of &quot;WINE Program Loader&quot; by default. WRONG!"
date: 2009-02-28
forum: General Help
---

### Post by emarkay on 2009-02-28
Wine Programs aren't working  now fr me.

I founs that the reason is that they (the ".EXE" programs) aren't "automagically" being opened by WINE, but with the "Archive Manager.

I found this by Right Clicking on the Wine EXE file.  This opens the "Archive Manager" as the default application, not "Wine Windows Program Loader" as it used to.  

I see a bunch of posts on this (and many critical WINE-ers), but apparently the problem is somehow WINE isn't "triggering" "Open With" as it should. I have confirmed this with the native 8.10 version and the latest WINE from wine HQ.

So, how do I change all my ".exe" to open with WINE instead of "Archive Manager"

---

### Post by emarkay on 2009-02-28
Anyone?

---

### Post by MarblePanther on 2009-02-28
Simply right-click on it and choose open with other application, and choose wine.

---

### Post by emarkay on 2009-03-02
OK, That's a given - I figured that one out already...

the issue is WHY IS IT NOT DOING WHAT IT IS SUPPOSED TO DO - like it did before...

AND HOW DO I FIX IT PERMANENTLY?

---

### Post by TeoBigusGeekus on 2009-03-02
Right click it->Properties->Open with Tab.

---

### Post by soxs on 2009-03-02
because it's fine, many .exe files are actually packed and therefor it's content can be viewed with archivemanager... (see BIOS related stuff, which is bugfix content for any linux user, not only those who need to get .exe files running)

---

### Post by emarkay on 2009-03-02
?????

OK - what's missing here?

I used to be able to install DOS programs in WINE (Irfanview, for example) and then when I clicked on the appropriate item, the WINE program loaded.

Something has changed here and now I can not get the program to install, because UBUNTU thinks it 's an archive - and I was always able to this before.

Here's what I get when I try to insatall this program in WINE:

 wine  iview423_setup.exe
fixme:advapi:CheckTokenMembership ((nil) 0x126d38 0x32f31c) stub!
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:system:SystemParametersInfoW Unimplemented action: 88 (SPI_SETICONS)
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
wine: Unhandled page fault on read access to 0x03c0000c at address 0x7ebbf57d (thread 0030), starting debugger...
Unhandled exception: page fault on read access to 0x03c0000c in 32-bit code (0x7ebbf57d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ebbf57d ESP:0033e2c0 EBP:0033e2e8 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:7ebe9ff4 ECX:7ebf20e0 EDX:7ebf20e4
 ESI:03c00004 EDI:00000384
Stack dump:
0x0033e2c0:  00000384 00000000 000004cc 00000017
0x0033e2d0:  00000090 00120a20 00120a20 7ee04ff4
0x0033e2e0:  7ec9b790 00135910 0033e368 7ed8760a
0x0033e2f0:  00000384 00000018 0033e344 00000018
0x0033e300:  00000018 0000045c 00000030 00000060
0x0033e310:  00220326 7ee04ff4 000004b4 00135910
Backtrace:
=>0 0x7ebbf57d GetObjectW+0x4d() in gdi32 (0x0033e2e8)
  1 0x7ed8760a ImageList_AddMasked+0xaa() in comctl32 (0x0033e368)
  2 0x00460997 in i_view32 (+0x60997) (0x00000378)
  3 0x00000000 (0x00000000)
0x7ebbf57d GetObjectW+0x4d in gdi32: movl	0x8(%esi),%eax
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  400000-  542000	Export          i_view32
ELF	7b800000-7b93f000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e0b2000-7e0b6000	Deferred        libgpg-error.so.0
ELF	7e0b6000-7e11f000	Deferred        libgcrypt.so.11
ELF	7e11f000-7e131000	Deferred        libtasn1.so.3
ELF	7e131000-7e145000	Deferred        libresolv.so.2
ELF	7e145000-7e149000	Deferred        libkeyutils.so.1
ELF	7e149000-7e152000	Deferred        libkrb5support.so.0
ELF	7e152000-7e184000	Deferred        libcrypt.so.1
ELF	7e184000-7e221000	Deferred        libgnutls.so.26
ELF	7e221000-7e245000	Deferred        libk5crypto.so.3
ELF	7e245000-7e2d7000	Deferred        libkrb5.so.3
ELF	7e2d7000-7e301000	Deferred        libgssapi_krb5.so.2
ELF	7e301000-7e337000	Deferred        libcups.so.2
ELF	7e392000-7e3c5000	Deferred        uxtheme<elf>
  \-PE	7e3a0000-7e3c5000	\               uxtheme
ELF	7e3c5000-7e3ce000	Deferred        libxcursor.so.1
ELF	7e3ce000-7e3d3000	Deferred        libxfixes.so.3
ELF	7e3d3000-7e3d7000	Deferred        libxcomposite.so.1
ELF	7e3d7000-7e3de000	Deferred        libxrandr.so.2
ELF	7e3de000-7e3e8000	Deferred        libxrender.so.1
ELF	7e3e8000-7e3ee000	Deferred        libxxf86vm.so.1
ELF	7e3ee000-7e40f000	Deferred        imm32<elf>
  \-PE	7e3f0000-7e40f000	\               imm32
ELF	7e40f000-7e428000	Deferred        libxcb.so.1
ELF	7e428000-7e517000	Deferred        libx11.so.6
ELF	7e517000-7e526000	Deferred        libxext.so.6
ELF	7e526000-7e53e000	Deferred        libice.so.6
ELF	7e53e000-7e547000	Deferred        libsm.so.6
ELF	7e550000-7e554000	Deferred        libcom_err.so.2
ELF	7e556000-7e5f2000	Deferred        winex11<elf>
  \-PE	7e560000-7e5f2000	\               winex11
ELF	7e628000-7e64f000	Deferred        libexpat.so.1
ELF	7e64f000-7e67c000	Deferred        libfontconfig.so.1
ELF	7e67c000-7e67f000	Deferred        libxinerama.so.1
ELF	7e68b000-7e6a1000	Deferred        libz.so.1
ELF	7e6a1000-7e717000	Deferred        libfreetype.so.6
ELF	7e717000-7e77e000	Deferred        rpcrt4<elf>
  \-PE	7e720000-7e77e000	\               rpcrt4
ELF	7e77e000-7e890000	Deferred        ole32<elf>
  \-PE	7e7a0000-7e890000	\               ole32
ELF	7e890000-7e8c6000	Deferred        winspool<elf>
  \-PE	7e8a0000-7e8c6000	\               winspool
ELF	7e8c6000-7e924000	Deferred        shlwapi<elf>
  \-PE	7e8d0000-7e924000	\               shlwapi
ELF	7e924000-7eab1000	Deferred        shell32<elf>
  \-PE	7e930000-7eab1000	\               shell32
ELF	7eab1000-7eb62000	Deferred        comdlg32<elf>
  \-PE	7eac0000-7eb62000	\               comdlg32
ELF	7eb62000-7ec03000	Export          gdi32<elf>
  \-PE	7eb70000-7ec03000	\               gdi32
ELF	7ec03000-7ed52000	Deferred        user32<elf>
  \-PE	7ec20000-7ed52000	\               user32
ELF	7ed52000-7ee19000	Export          comctl32<elf>
  \-PE	7ed60000-7ee19000	\               comctl32
ELF	7ee19000-7ee6e000	Deferred        advapi32<elf>
  \-PE	7ee30000-7ee6e000	\               advapi32
ELF	7ee6e000-7ee7a000	Deferred        libnss_files.so.2
ELF	7ee7a000-7ee93000	Deferred        libnsl.so.1
ELF	7ee93000-7ee9c000	Deferred        libnss_compat.so.2
ELF	7ee9c000-7eea1000	Deferred        libxdmcp.so.6
ELF	7eea1000-7eea4000	Deferred        libxcb-xlib.so.0
ELF	7efcb000-7eff1000	Deferred        libm.so.6
ELF	7eff2000-7eff5000	Deferred        libxau.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d14000-b7d18000	Deferred        libdl.so.2
ELF	b7d18000-b7e76000	Deferred        libc.so.6
ELF	b7e77000-b7e90000	Deferred        libpthread.so.0
ELF	b7e9f000-b7fda000	Deferred        libwine.so.1
ELF	b7fdc000-b7ff9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
0000002f (D) C:\Program Files\IrfanView\i_view32.exe
	00000030    0 <==
Backtrace:
=>0 0x7ebbf57d GetObjectW+0x4d() in gdi32 (0x0033e2e8)
  1 0x7ed8760a ImageList_AddMasked+0xaa() in comctl32 (0x0033e368)
  2 0x00460997 in i_view32 (+0x60997) (0x00000378)
  3 0x00000000 (0x00000000)


I know this isn't the WINE forum, but can ANYONE help?

---

### Post by emarkay on 2009-03-02
Here's my post on the WINE forum, so far no ideas there either.

[http://forum.winehq.org/viewtopic.php?p=20624#20624](http://forum.winehq.org/viewtopic.php?p=20624#20624)

---

### Post by emarkay on 2009-03-02
A clue?

I can get the program to open when I used "GKSUDO" (root) Nautilus and right click on "Open with Wine Windows ...", but it does NOT work in Nautilus, or from the "Application/Wine/Browse..." (It puts "opening" on the taskbar for a few seconds then times out and goes away.)

Also, I am still trying to make the ".EXE" programs DEFAULT to "Wine" and NOT "Archive Manager"

---

### Post by MarblePanther on 2009-03-02
> **TeoBigusGeekus said:**
> Right click it->Properties->Open with Tab.

If this isn't working, then you should probably file a bug report, because that is odd behaviour.

---

### Post by emarkay on 2009-03-03
> **MarblePanther said:**
> If this isn't working, then you should probably file a bug report, because that is odd behaviour.

Thanks -- I agree, and I am rather computer literate.

But who's bug???

Wine or Ubuntu?

---

### Post by Slim Odds on 2009-03-03
> **emarkay said:**
> But who's bug???

Wine or Ubuntu?

If it is really a bug, sounds like GNOME.

I'm doubting it's a bug.

Can you run us through the whole process again? I think that you did something wrong somewhere along the way......

I'm specifically wondering about the "GKSUDO". There should never have been a need for that.

---

### Post by emarkay on 2009-03-03
> **Slim Odds said:**
> If it is really a bug, sounds like GNOME. I'm doubting it's a bug.

Can you run us through the whole process again? I think that you did something wrong somewhere along the way...... I'm specifically wondering about the "GKSUDO". There should never have been a need for that.

I agree...

OK  I have "irfanview_plugins_422_setup.exe" and "iview423_setup.exe" in my "DOWNLOADED" directory.

*****Of course I JUST noticed the "open with" under PROPERTIES LET ME CHANGE THE ASSOCIATION  - FINALLY!!!*******


First, I confirm that "mfc42.dll" is copied to the "/home/<username>/.wine/dosdevices/c:/windows/system32" directory, and is "native/builtin" in "Wine/Configuration/Libraries"

1. Open TERMINAL
2. Type "cd \DOWNLOADED"
3. Type " wine iview423_setup.exe"
4. The Windows Application Installation begines...
5. Set destinaton folder: C:\Program Files\IrfanView\ (default)
6. Hit "NEXT
7. Select "images only": as  I always do (sets image associations to Ifranview), hit "NEXT".
8. Deselect Google Install Apps as I always do, hit "NEXT".
9. Select "INI folder" as "Irfanview folder"  (Surely it's not this...) I recall I always leave thsi, defailt, setting. hit "NEXT".
10. Confirm changing of image file associations with "YES".
11. Hit "DONE" and browser opens to Irfan page as it always does.  "Start Irfanview" is checked (as default) and this SHOULD also open program, too.
12. Close Browser, and no Irfanview.


This is the TERMINAL output:

"wine iview423_setup.exe

fixme:advapi:CheckTokenMembership ((nil) 0x126d38 0x32f31c) stub!
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:system:SystemParametersInfoW Unimplemented action: 88 (SPI_SETICONS)
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
wine: Unhandled page fault on read access to 0x03c0000c at address 0x7ebbf57d (thread 0030), starting debugger...
Unhandled exception: page fault on read access to 0x03c0000c in 32-bit code (0x7ebbf57d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ebbf57d ESP:0033e2c0 EBP:0033e2e8 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:7ebe9ff4 ECX:7ebf20e0 EDX:7ebf20e4
 ESI:03c00004 EDI:00000384
Stack dump:
0x0033e2c0:  00000384 00000000 000004cc 00000017
0x0033e2d0:  00000090 00120a20 00120a20 7ee04ff4
0x0033e2e0:  7ec9b790 00135b18 0033e368 7ed8760a
0x0033e2f0:  00000384 00000018 0033e344 00000018
0x0033e300:  00000018 0000045c 00000030 00000060
0x0033e310:  00220326 7ee04ff4 000004b4 00135b18
Backtrace:
=>0 0x7ebbf57d GetObjectW+0x4d() in gdi32 (0x0033e2e8)
  1 0x7ed8760a ImageList_AddMasked+0xaa() in comctl32 (0x0033e368)
  2 0x00460997 in i_view32 (+0x60997) (0x00000378)
  3 0x00000000 (0x00000000)
0x7ebbf57d GetObjectW+0x4d in gdi32: movl	0x8(%esi),%eax
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  400000-  542000	Export          i_view32
ELF	7b800000-7b93f000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e0b2000-7e0b6000	Deferred        libgpg-error.so.0
ELF	7e0b6000-7e11f000	Deferred        libgcrypt.so.11
ELF	7e11f000-7e131000	Deferred        libtasn1.so.3
ELF	7e131000-7e145000	Deferred        libresolv.so.2
ELF	7e145000-7e149000	Deferred        libkeyutils.so.1
ELF	7e149000-7e152000	Deferred        libkrb5support.so.0
ELF	7e152000-7e184000	Deferred        libcrypt.so.1
ELF	7e184000-7e221000	Deferred        libgnutls.so.26
ELF	7e221000-7e245000	Deferred        libk5crypto.so.3
ELF	7e245000-7e2d7000	Deferred        libkrb5.so.3
ELF	7e2d7000-7e301000	Deferred        libgssapi_krb5.so.2
ELF	7e301000-7e337000	Deferred        libcups.so.2
ELF	7e392000-7e3c5000	Deferred        uxtheme<elf>
  \-PE	7e3a0000-7e3c5000	\               uxtheme
ELF	7e3c5000-7e3ce000	Deferred        libxcursor.so.1
ELF	7e3ce000-7e3d3000	Deferred        libxfixes.so.3
ELF	7e3d3000-7e3d7000	Deferred        libxcomposite.so.1
ELF	7e3d7000-7e3de000	Deferred        libxrandr.so.2
ELF	7e3de000-7e3e8000	Deferred        libxrender.so.1
ELF	7e3e8000-7e3ee000	Deferred        libxxf86vm.so.1
ELF	7e3ee000-7e40f000	Deferred        imm32<elf>
  \-PE	7e3f0000-7e40f000	\               imm32
ELF	7e40f000-7e428000	Deferred        libxcb.so.1
ELF	7e428000-7e517000	Deferred        libx11.so.6
ELF	7e517000-7e526000	Deferred        libxext.so.6
ELF	7e526000-7e53e000	Deferred        libice.so.6
ELF	7e53e000-7e547000	Deferred        libsm.so.6
ELF	7e552000-7e556000	Deferred        libcom_err.so.2
ELF	7e556000-7e5f2000	Deferred        winex11<elf>
  \-PE	7e560000-7e5f2000	\               winex11
ELF	7e628000-7e64f000	Deferred        libexpat.so.1
ELF	7e64f000-7e67c000	Deferred        libfontconfig.so.1
ELF	7e68b000-7e6a1000	Deferred        libz.so.1
ELF	7e6a1000-7e717000	Deferred        libfreetype.so.6
ELF	7e717000-7e77e000	Deferred        rpcrt4<elf>
  \-PE	7e720000-7e77e000	\               rpcrt4
ELF	7e77e000-7e890000	Deferred        ole32<elf>
  \-PE	7e7a0000-7e890000	\               ole32
ELF	7e890000-7e8c6000	Deferred        winspool<elf>
  \-PE	7e8a0000-7e8c6000	\               winspool
ELF	7e8c6000-7e924000	Deferred        shlwapi<elf>
  \-PE	7e8d0000-7e924000	\               shlwapi
ELF	7e924000-7eab1000	Deferred        shell32<elf>
  \-PE	7e930000-7eab1000	\               shell32
ELF	7eab1000-7eb62000	Deferred        comdlg32<elf>
  \-PE	7eac0000-7eb62000	\               comdlg32
ELF	7eb62000-7ec03000	Export          gdi32<elf>
  \-PE	7eb70000-7ec03000	\               gdi32
ELF	7ec03000-7ed52000	Deferred        user32<elf>
  \-PE	7ec20000-7ed52000	\               user32
ELF	7ed52000-7ee19000	Export          comctl32<elf>
  \-PE	7ed60000-7ee19000	\               comctl32
ELF	7ee19000-7ee6e000	Deferred        advapi32<elf>
  \-PE	7ee30000-7ee6e000	\               advapi32
ELF	7ee6e000-7ee7a000	Deferred        libnss_files.so.2
ELF	7ee7a000-7ee93000	Deferred        libnsl.so.1
ELF	7ee93000-7ee9c000	Deferred        libnss_compat.so.2
ELF	7ee9f000-7eea4000	Deferred        libxdmcp.so.6
ELF	7efcb000-7eff1000	Deferred        libm.so.6
ELF	7eff2000-7eff5000	Deferred        libxinerama.so.1
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cf0000-b7cf3000	Deferred        libxcb-xlib.so.0
ELF	b7cf3000-b7cf6000	Deferred        libxau.so.6
ELF	b7cf9000-b7cfd000	Deferred        libdl.so.2
ELF	b7cfd000-b7e5b000	Deferred        libc.so.6
ELF	b7e5c000-b7e75000	Deferred        libpthread.so.0
ELF	b7e84000-b7fbf000	Deferred        libwine.so.1
ELF	b7fc1000-b7fde000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
0000002f (D) C:\Program Files\IrfanView\i_view32.exe
	00000030    0 <==
Backtrace:
=>0 0x7ebbf57d GetObjectW+0x4d() in gdi32 (0x0033e2e8)
  1 0x7ed8760a ImageList_AddMasked+0xaa() in comctl32 (0x0033e368)
  2 0x00460997 in i_view32 (+0x60997) (0x00000378)
  3 0x00000000 (0x00000000)"

14. Program Icons and ".lnk" icons appear on desktop as normal.
15. Click on "Irfanview" icon, which once opened program, and "Starting Irfanview" appears in lower taskbar for about 10 seconds and then goes away.
16. Click "Applicatinos/Wine/Programs/Irfanview" and the same thing happens.
17. Manually go to "/home/<username>/.wine/dosdevices/c:/Program Files/IrfanView" and right click on "i_view32.exe" and select "open with Wine Windows Program Loader" and the same thing happens.
18. in TERMINAL type gksudo nautilus and enter password.
19. manually go to "/home/<username>/.wine/drive_c/Program Files/IrfanView" and then right click on "i_view32.exe" and select open with Wine Windows Program Loader" and the same thing happens.  

(GKSUDO DOES NOT WORK NOW...)

BTW, This is my TERMINAL WINDOW NOW. IS THIS OK???

"SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSInitializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nautilus:13344): WARNING **: Unable to add monitor: Operation not supported

** (nautilus:13344): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

wine: Unhandled page fault on read access to 0x03e0000c at address 0x7ebbf57d (thread 0018), starting debugger...
wine: Unhandled page fault on read access to 0x03e0000c at address 0x7ebbf57d (thread 0018), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7ebbf57d"



So now what?????????????????

---

### Post by emarkay on 2009-03-04
More ideas uncovered, still looking for solution.

This is strange...

Also posted on Irfanview forum.
[http://en.irfanview-forum.de/vb/showthread.php?p=19523#post19523](http://en.irfanview-forum.de/vb/showthread.php?p=19523#post19523)

---

### Post by emarkay on 2009-03-04
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)

Fix for 4.20+
by Craig Mann on Monday January 5th 2009, 19:36
This should work for 4.20. It is verified to work with the newest version to date (4.23). I have discovered a workaround for the crash caused by toolbar skins.

Install IrfanView and make sure the "Set INI file" setting is set to "IrfanView folder" so it will be easy to find. Once installed edit i_view32.ini in your installation folder and delete the lines following "[Toolbar]" at the bottom. Save and it should now start without a hitch.

---

### Post by emarkay on 2009-03-04
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)	
Fix for 4.20+
by Craig Mann on Monday January 5th 2009, 19:36
This should work for 4.20. It is verified to work with the newest version to date (4.23). I have discovered a workaround for the crash caused by toolbar skins.

Install IrfanView and make sure the "Set INI file" setting is set to "IrfanView folder" so it will be easy to find. Once installed edit i_view32.ini in your installation folder and delete the lines following "[Toolbar]" at the bottom. Save and it should now start without a hitch.

Also - not marked SOLVED because:

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

