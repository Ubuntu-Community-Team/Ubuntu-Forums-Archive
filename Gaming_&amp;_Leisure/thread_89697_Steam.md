---
title: "Steam"
date: 2005-11-13
forum: Gaming &amp; Leisure
---

### Post by Nicktu on 2005-11-13
Does anyone know how i can install Steam on my linux box to i can play the game counterstrike, there is no download for linux except for the beta version, but ive heard there are ways around it! please help

---

### Post by stoffe on 2005-11-13
Just follow instructions [here]("http://appdb.winehq.org/appview.php?versionId=1554&iTestingId=3") or [here]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17"). Then install CS from within Steam as per usual. 

I recommend getting the newest wine directly from the Wine HQ. Also, yes, it might freeze on updating itself as it says in the second link, but it will work eventually, just keep trying.

I also made a modified startup script based on the one in the second link, something like this:
```
#!/bin/bash
cd .wine/drive_c/Program\ Files/Steam/
WINEDEBUG="-all" wine Steam.exe -applaunch 10 -heapsize 300000 &
```

Works just fine actually, although I think the performance might be a bit lower than on Windows. Have no Win partition anymore so can't test it for sure, just seem to recall quite a bit higher numbers for fps and so on...

Also remember to get real drivers for your card, so you have real 3D acceleration.

---

### Post by Nicktu on 2005-11-13
thanks! but i went through that process and i have the source made and the binary in the synaptic package manager, but then it tells me

Installing from the WineHQ APT Repository with the console:

If your system doesn't use a graphical package manager like Synaptic, you will need to edit APT's configuration file by hand. You will need root access to do this and run the commands below. Switch to root by typing 'su'. If you are an Ubuntu user, you can instead precede each command with 'sudo'. Now, use your favorite text editor to open the file /etc/apt/sources.list or use the console editor by typing 'nano /etc/apt/sources.list' and then add the following lines to the end:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

Then, you can run 'apt-get update' to update APT's package information. Finally, to install Wine, do 'apt-get install wine'.

If you want to make sure that apt-get will install the WineHQ wine package instead of the Debian wine package (which usually has the same version), then add something like the following entry to /etc/apt/preferences:

Package: wine
Pin: release l=WineHQ APT Repository
Pin-Priority: 1000

Or alternatively use a modified rule to adjust the installation relationship between WineHQ and Debian packages in a different way.

im not sure what any of that means, sorry man im a linux noobie

---

### Post by stoffe on 2005-11-13
If you have added those URLs like it says, in Synaptic, all you need to do is search for the package "wine" in Synaptic and install (or upgrade) it. You can ignore the rest of the instructions, that is just another way to do it.

---

### Post by Nicktu on 2005-11-14
im having some trouble installing the wine CVS is there an easier way to install that? cuz my noobie-ness is kicking in, its complicated because of the changeing of the file name, or is there a step by step process somewhere thats easier?

---

### Post by stoffe on 2005-11-14
No need to go with Wine CVS. Just follow the instructions here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

In short, add a new **custom** repository in Synaptic, with this line:
```
deb http://wine.sourceforge.net/apt breezy/
```
You don't need the source version.

Then, in Synaptic, find and install the package **wine**. That should be all, after that you can proceed with installing Steam itself.

---

### Post by alexmap on 2005-12-11
I installed Steam using the guides provided [LinuX gamers website], but I keep getting this error [Steam update gets to 26% and stops there, every time]:

```
Steam.exe (main exception): ERROR: delete of Steam.exe failed, Win32 Error 32 "Sharing violation"
```

Someone else on the forums had a similar problem, they fixed it by deleting Steam.exe and renaming the SteamNew.exe file [to Steam.exe] that was downloaded during the "update." I tried this as well, but it didn't work...

---

### Post by linkunderscore on 2005-12-11
[QUOTE=alexmap]I installed Steam using the guides provided [LinuX gamers website], but I keep getting this error [Steam update gets to 26% and stops there, every time]:

```
Steam.exe (main exception): ERROR: delete of Steam.exe failed, Win32 Error 32 "Sharing violation"
```

Someone else on the forums had a similar problem, they fixed it by deleting Steam.exe and renaming the SteamNew.exe file [to Steam.exe] that was downloaded during the "update." I tried this as well, but it didn't work...[/QUOTE]


do this:
```
killall -9 wine-preloader ; wineboot

```

---

### Post by alexmap on 2005-12-11
That didn't work either...

```
err:seh:setup_exception stack overflow 36 bytes in thread 003b eip 00446fe7 esp 7d74bfdc stack 0x7d74b000-0x7d84c000

err:seh:setup_exception stack overflow 0 bytes in thread 0037 eip 7bebd0d9 esp 7f9e1000 stack 0x7f9e0000-0x7fae0000
```

That's the error that shows up in the terminal, then the "Win32 error 32" message comes out.

EDIT: Never mind, it sort of worked... but now something else isn't working; here's a screenshot of what appears in the terminal. [Thanks, by the way]

---

### Post by YokoZar on 2005-12-11
> **alexmap]
EDIT: Never mind, it sort of worked... but now something else isn't working said:**
> 
Are you attempting to run steam off of some other hard disk with Windows on it?

That won't work anymore than running applications over a shared disk in Windows.  You need to install applications fresh into Wine's virtual windows drive.

---

### Post by alexmap on 2005-12-12
[QUOTE=YokoZar]Are you attempting to run steam off of some other hard disk with Windows on it?

That won't work anymore than running applications over a shared disk in Windows.  You need to install applications fresh into Wine's virtual windows drive.[/QUOTE]

No, I'm using the Steam installer and everything to install it into Wine's "drive_c" and everything, although I do have Steam on another partition.

EDIT: Tried to get this thing working once again, had an error (something about shdocvw.dll requiring a "CRYPTUI.dll", so I copied the file from my actual Windows partition and placed it in Wine's "windows" folder) that I got around, and steam starts... but there's no text. Here's another screenshot...

---

### Post by TrinitronX on 2005-12-12
It looks like you need some windows ttf fonts installed into wine or your system.  I believe the two that are needed are: MARLETT.TTF and tahoma.ttf.
I just copied these 2 fonts over from my windows hard drive into the 'drive_c/windows/Fonts' directory in my cvscedega folder.

I have been trying to get steam working for a while now too... but I've had no luck installing it or using the version I copied over from my windows drive.
I am using cvscedega for it instead of wine (I heard somewhere it may work better than wine.. but haven't had any luck at all with it :roll:)
I can get the program to run, but I get some errors when running it, both in my terminal and an actual 'windows' error :P:
```
trinitronx@Arcturus:~/.cvscedega/drive_c/Program Files/Steam$ cvscedega Steam.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:DEVICE_Open Unknown/unsupported VxD GDPERF. Try --winver nt40 or win31 !
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win:GetProcessWindowStation (void): stub
fixme:win32:GetUserObjectInformationA (0x1 1 0xb79ff2bc 12 0xb79ff2c8),stub!
fixme:dialog:MSGBOX_OnInit task modal msgbox ! Not modal yet.

```

Attached is an image of both my terminal and the error window I'm getting.

---

### Post by niels on 2006-01-02
I have installed Steam with the insctruction sugested in this thread

[QUOTE=stoffe]Just follow instructions [here]("http://appdb.winehq.org/appview.php?versionId=1554&iTestingId=3") or [here]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17"). Then install CS from within Steam as per usual. 
[/QUOTE]

It halted all the time. Then there it got possible to update Wine to 0.9.4, and so I did. But now I get the following message, when I try to start Steam:
> niels@nielslaptop:~$ cd '.wine/drive_c/Program Files/Steam'
[email]niels@nielslaptop:~/.wine[/email]/drive_c/Program Files/Steam$ wine steam.exe err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
wine: Unhandled page fault on read access to 0x0000000c at address 0x6a301c16 (thread 0020), starting debugger...
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x0000000c in 32-bit code (0x6a301c16).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:12af GS:0033
 EIP:6a301c16 ESP:6939a9a8 EBP:6939a9b8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:7beffc60 EBX:6a317520 ECX:00000000 EDX:00000000
 ESI:6c0bd890 EDI:00000000
Stack dump:
0x6939a9a8:  6a311b90 6a317520 6c0bd890 00000003
0x6939a9b8:  6939a9d8 6a311bb8 6a2e0000 00000003
0x6939a9c8:  00000000 7bef41b0 6c0bd890 6a311b90
0x6939a9d8:  6939a9f8 7bebffe5 6a2e0000 00000003
0x6939a9e8:  00000000 00000000 00000000 7bef41b0
0x6939a9f8:  6939aa84 7bec0d9a 6a311b90 6a2e0000
0255: sel=12af base=6939c000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x6a301c16 DllMain+0x1d6 in msvcrt (0x6a301c16)
  2 0x6a311bb8 in msvcrt (+0x31bb8) (0x6a311bb8)
  3 0x7bebffe5 call_dll_entry_point+0x15 in ntdll (0x7bebffe5)
  4 0x7bec0d9a in ntdll (+0x20d9a) (0x7bec0d9a)
  5 0x7bec14e9 LdrShutdownThread+0x99 in ntdll (0x7bec14e9)
  6 0x7bedcdc5 RtlExitUserThread+0x15 in ntdll (0x7bedcdc5)
  7 0x7fcf72e5 in kernel32 (+0x672e5) (0x7fcf72e5)
  8 0x7fcf7a4d in kernel32 (+0x67a4d) (0x7fcf7a4d)
  9 0x7bedd75f in ntdll (+0x3d75f) (0x7bedd75f)
  10 0xb7efe361 start_thread+0x81 in libpthread.so.0 (0xb7efe361)
  11 0xb7e92bde __clone+0x5e in libc.so.6 (0xb7e92bde)
0x6a301c16 DllMain+0x1d6 in msvcrt: movl        0xc(%edi),%esi
Modules:
Module  Address                 Debug info      Name (154 modules)
PE      0x00400000-00538000     Deferred        steam
PE      0x10000000-1027f000     Deferred        steamui
PE      0x30000000-30027000     Deferred        nspr4
PE      0x55900000-55961000     Deferred        msvcp60
PE      0x69a20000-69a2d000     Deferred        jar50
PE      0x69a30000-69a3a000     Deferred        cookie
PE      0x69b60000-69b68000     Deferred        pipboot
PE      0x69b70000-69b90000     Deferred        imglib2
PE      0x69ba0000-69de9000     Deferred        gklayout
PE      0x69df0000-69e13000     Deferred        gkgfxwin
PE      0x69e20000-69e37000     Deferred        gkgfx
PE      0x69e40000-69e62000     Deferred        gkwidget
PE      0x69e70000-69e7e000     Deferred        webbrwsr
PE      0x69e80000-69ea7000     Deferred        docshell
PE      0x69eb0000-69f6a000     Deferred        uconv
PE      0x69f70000-69fa4000     Deferred        gkparser
PE      0x69fb0000-69fc9000     Deferred        rdf
PE      0x69fd0000-69fe0000     Deferred        chrome
PE      0x69ff0000-6a004000     Deferred        xpcom_compat
PE      0x6a010000-6a017000     Deferred        xpcom_compat_c
PE      0x6a020000-6a02e000     Deferred        profile
PE      0x6a030000-6a05d000     Deferred        i18n
PE      0x6a060000-6a070000     Deferred        mozz
PE      0x6a080000-6a0f6000     Deferred        necko
PE      0x6a100000-6a10d000     Deferred        xppref32
PE      0x6a110000-6a13e000     Deferred        xpc3250
PE      0x6a140000-6a14f000     Deferred        caps
PE      0x6a150000-6a1a6000     Deferred        js3250
PE      0x6a1b0000-6a1ce000     Deferred        embedcomponents
PE      0x6a1f0000-6a1f6000     Deferred        plds4
PE      0x6a200000-6a207000     Deferred        plc4
PE      0x6a210000-6a271000     Deferred        xpcom_core
PE      0x6a280000-6a286000     Deferred        xpcom
PE      0x6a290000-6a2c3000     Deferred        mozctl
ELF     0x6a2d3000-6a333000     Export          msvcrt<elf>
  \-PE  0x6a2e0000-6a333000     \               msvcrt
ELF     0x6a333000-6a360000     Deferred        shdocvw<elf>
  \-PE  0x6a340000-6a360000     \               shdocvw
PE      0x6a360000-6a4ae000     Deferred        serverbrowser
PE      0x6a4b0000-6a5a7000     Deferred        friendsui
PE      0x6aa10000-6aa16000     Deferred        mozctlx
ELF     0x6aa25000-6aa3e000     Deferred        wsock32<elf>
  \-PE  0x6aa30000-6aa3e000     \               wsock32
ELF     0x6afdd000-6b00d000     Deferred        crypt32<elf>
  \-PE  0x6aff0000-6b00d000     \               crypt32
ELF     0x6b00d000-6b040000     Deferred        rsaenh<elf>
  \-PE  0x6b020000-6b040000     \               rsaenh
PE      0x6b040000-6b10c000     Deferred        steamclient
ELF     0x789b6000-789be000     Deferred        libxrender.so.1
ELF     0x7be8c000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7caac000-7cac0000     Deferred        msimg32<elf>
  \-PE  0x7cab0000-7cac0000     \               msimg32
PE      0x7cac0000-7cb4d000     Deferred        vgui2
PE      0x7cb50000-7cb88000     Deferred        filesystem_steam
ELF     0x7cb8b000-7cba0000     Deferred        psapi<elf>
  \-PE  0x7cb90000-7cba0000     \               psapi
ELF     0x7cdde000-7ce20000     Deferred        wineoss<elf>
  \-PE  0x7cdf0000-7ce20000     \               wineoss
PE      0x7ce20000-7ce5e000     Deferred        tier0_s
ELF     0x7d1a2000-7d1b7000     Deferred        midimap<elf>
  \-PE  0x7d1b0000-7d1b7000     \               midimap
ELF     0x7d657000-7d679000     Deferred        msacm32<elf>
  \-PE  0x7d660000-7d679000     \               msacm32
ELF     0x7d679000-7d690000     Deferred        msacm<elf>
  \-PE  0x7d680000-7d690000     \               msacm
PE      0x7d690000-7d6cb000     Deferred        vstdlib_s
ELF     0x7d6d7000-7d758000     Deferred        winmm<elf>
  \-PE  0x7d6e0000-7d758000     \               winmm
ELF     0x7d758000-7d76b000     Deferred        libresolv.so.2
ELF     0x7d76b000-7d77f000     Deferred        mswsock<elf>
  \-PE  0x7d770000-7d77f000     \               mswsock
ELF     0x7d77f000-7d781000     Deferred        iso8859-1.so
ELF     0x7daac000-7dadc000     Deferred        uxtheme<elf>
  \-PE  0x7dab0000-7dadc000     \               uxtheme
ELF     0x7dadc000-7db28000     Deferred        libgcrypt.so.11
ELF     0x7db28000-7db38000     Deferred        libtasn1.so.2
ELF     0x7db38000-7db9a000     Deferred        libgnutls.so.11
ELF     0x7db9a000-7dbb7000     Deferred        libcups.so.2
ELF     0x7dc09000-7dc12000     Deferred        libxcursor.so.1
ELF     0x7dc13000-7dc18000     Deferred        libnss_dns.so.2
ELF     0x7dc20000-7dc3b000     Deferred        imm32<elf>
  \-PE  0x7dc30000-7dc3b000     \               imm32
ELF     0x7dc3b000-7dc57000     Deferred        ximcp.so.2
ELF     0x7e559000-7e75c000     Deferred        i915_dri.so
ELF     0x7e75c000-7e763000     Deferred        libdrm.so.1
ELF     0x7e763000-7e7c9000     Deferred        libgl.so.1
ELF     0x7e7c9000-7e7cd000     Deferred        libxdmcp.so.6
ELF     0x7e7cd000-7e88d000     Deferred        libx11.so.6
ELF     0x7e88d000-7e89a000     Deferred        libxext.so.6
ELF     0x7e89a000-7e8b3000     Deferred        libice.so.6
ELF     0x7e8b3000-7e8ba000     Deferred        libsm.so.6
ELF     0x7e8ba000-7e937000     Deferred        winex11<elf>
  \-PE  0x7e8d0000-7e937000     \               winex11
ELF     0x7e937000-7e956000     Deferred        libexpat.so.1
ELF     0x7e956000-7e984000     Deferred        libfontconfig.so.1
ELF     0x7e984000-7e998000     Deferred        libz.so.1
ELF     0x7e998000-7ea02000     Deferred        libfreetype.so.6
ELF     0x7ea02000-7ea16000     Deferred        oleacc<elf>
  \-PE  0x7ea10000-7ea16000     \               oleacc
ELF     0x7ea16000-7ea2a000     Deferred        lz32<elf>
  \-PE  0x7ea20000-7ea2a000     \               lz32
ELF     0x7ea2a000-7ea42000     Deferred        version<elf>
  \-PE  0x7ea30000-7ea42000     \               version
ELF     0x7ea42000-7ea5b000     Deferred        oledlg<elf>
  \-PE  0x7ea50000-7ea5b000     \               oledlg
ELF     0x7ea5b000-7eae8000     Deferred        oleaut32<elf>
  \-PE  0x7ea70000-7eae8000     \               oleaut32
ELF     0x7eae8000-7eb97000     Deferred        comctl32<elf>
  \-PE  0x7eaf0000-7eb97000     \               comctl32
ELF     0x7eb97000-7ebdb000     Deferred        rpcrt4<elf>
  \-PE  0x7ebb0000-7ebdb000     \               rpcrt4
ELF     0x7ebdb000-7ec61000     Deferred        ole32<elf>
  \-PE  0x7ebf0000-7ec61000     \               ole32
ELF     0x7ec61000-7ecb6000     Deferred        shlwapi<elf>
  \-PE  0x7ec70000-7ecb6000     \               shlwapi
ELF     0x7ecb6000-7ed74000     Deferred        shell32<elf>
  \-PE  0x7ecd0000-7ed74000     \               shell32
ELF     0x7ed74000-7ee06000     Deferred        comdlg32<elf>
  \-PE  0x7ed80000-7ee06000     \               comdlg32
ELF     0x7ee06000-7ee2e000     Deferred        winspool<elf>
  \-PE  0x7ee10000-7ee2e000     \               winspool
ELF     0x7ef14000-7f814000     Deferred        gdi32<elf>
  \-PE  0x7ef60000-7f814000     \               gdi32
ELF     0x7f814000-7f92d000     Deferred        user32<elf>
  \-PE  0x7f830000-7f92d000     \               user32
ELF     0x7f92d000-7f969000     Deferred        advapi32<elf>
  \-PE  0x7f940000-7f969000     \               advapi32
ELF     0x7f969000-7f987000     Deferred        iphlpapi<elf>
  \-PE  0x7f970000-7f987000     \               iphlpapi
ELF     0x7f987000-7f9b0000     Deferred        ws2_32<elf>
  \-PE  0x7f990000-7f9b0000     \               ws2_32
ELF     0x7fac2000-7fac5000     Deferred        libxau.so.6
ELF     0x7fac5000-7fad0000     Deferred        libgcc_s.so.1
ELF     0x7fad2000-7fad7000     Deferred        libxxf86vm.so.1
ELF     0x7fc74000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe80000-7fe85000     Deferred        libxxf86dga.so.1
ELF     0x7fe85000-7fe8f000     Deferred        libnss_files.so.2
ELF     0x7fe8f000-7fe98000     Deferred        libnss_nis.so.2
ELF     0x7fe98000-7fead000     Deferred        libnsl.so.1
ELF     0x7fead000-7feb6000     Deferred        libnss_compat.so.2
ELF     0x7feb9000-7febd000     Deferred        libgpg-error.so.0
ELF     0x7febd000-7fec1000     Deferred        libxfixes.so.3
ELF     0x7fec1000-7fec4000     Deferred        libxrandr.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7dc7000-b7dca000     Deferred        libdl.so.2
ELF     0xb7dca000-b7ef8000     Export          libc.so.6
ELF     0xb7ef9000-b7f0b000     Export          libpthread.so.0
ELF     0xb7f0b000-b7f25000     Deferred        libwine.so.1
ELF     0xb7f25000-b7f27000     Deferred        xlcutf8load.so.2
ELF     0xb7f36000-b7f4c000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Steam\steam.exe
        00000024    0
        00000021    0
        00000020    0 <==
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c    0
        00000019    0
        00000017    0
        00000016    1
        00000014    0
        00000013    0
        00000012    1
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        0000000b    0
        0000000a    0
        00000009    0
WineDbg terminated on pid 0x8
[email]niels@nielslaptop:~/.wine[/email]/drive_c/Program Files/Steam$


Is it because I updated Wine? Got the advise to install another version of Steam, but got the message, that Steam was allready registered. Wat does that mean?

---

### Post by zappa86 on 2006-01-02
thats the same error I have. I wonder if it has to do with the fact that I have an AMD64 proc instead of a good ol' intel one. (even though i'm running ia32 linux).

---

### Post by pharcyde on 2006-01-02
> thats the same error I have. I wonder if it has to do with the fact that I have an AMD64 proc instead of a good ol' intel one. (even though i'm running ia32 linux).

This error is a known error and is due to a regression in the 0.9.4 wine code.  It should be fixed in the next version of wine.  Use 0.9.3 or search the forums for the patch to fix the 0.9.4 code.

---

### Post by FizDev on 2006-01-04
[QUOTE=niels]It halted all the time.[/QUOTE]
Does it does that to everyone? Because I too have this problem, the game seems to work alright for 5 seconds then halt, wait, wait, works, halt, etc. I'm running it under Wine 0.9.4 but I don't seem to have the other errors. Would it be possible that it halts because I have an ATI or? :confused:

---

### Post by TrinitronX on 2006-01-05
i've finally gotten steam to work under my cvswine installation, however, when I run CS:S from steam, it is really laggy and slow.  I looked into the game's options menu, and saw that it was using a hardware mode of directX 8, but a software mode of directX 9.  I have an ATI 9800pro with the proprietary drivers installed.  fgl_glxgears works fine.

Is there anything I can do to either enable DirectX 9 support for my card, or force the game to run in DirectX 8 mode?  (I've already tried passing CS:S the "-dxlevel 81" flag)

---

### Post by niels on 2006-01-05
[QUOTE=pharcyde]This error is a known error and is due to a regression in the 0.9.4 wine code.  It should be fixed in the next version of wine.  Use 0.9.3 or search the forums for the patch to fix the 0.9.4 code.[/QUOTE]

Now Wine 0.9.5 is ready. And an update of Wine made it possible to starte Steam again. But it is still very slow, and halts all the time. And therefore it is impossible to use.
This is what my terminal writes when i run Steam:
> niels@nielslaptop:~$ cd '.wine/drive_c/Program Files/Steam'
[email]niels@nielslaptop:~/.wine[/email]/drive_c/Program Files/Steam$ wine steam.exe err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
err:ntdll:RtlpWaitForCriticalSection section 0x6c0523b4 "?" wait timed out in thread 001d, blocked by 0009, retrying (60 sec)
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless


Does anyone know if the problem can be identified from this?

Another problem...
When I close Steam (using the 'close cross'), Wine-Systray keeps running. How do I close this (the terminal looks like described abowe - it's not possible to write anyting)?

---

### Post by cb951303 on 2006-01-10
[QUOTE=TrinitronX]i've finally gotten steam to work under my cvswine installation, however, when I run CS:S from steam, it is really laggy and slow.  I looked into the game's options menu, and saw that it was using a hardware mode of directX 8, but a software mode of directX 9.  I have an ATI 9800pro with the proprietary drivers installed.  fgl_glxgears works fine.

Is there anything I can do to either enable DirectX 9 support for my card, or force the game to run in DirectX 8 mode?  (I've already tried passing CS:S the "-dxlevel 81" flag)[/QUOTE]
I have exactly the same problem
I also tried cedega 5.0.2 (commercial). it's the same thing but only with extra 5-10 fps 
any solution ?

---

### Post by Mr_Grieves on 2006-01-11
The "freezing" issue is a known problem. I created a bug report for at winehq about this. The problem appear after a Steam platform update in late december.

Running off-line should fix the problem for you, if you're not playing online..

More info:
[http://bugs.winehq.org/show_bug.cgi?id=4131](http://bugs.winehq.org/show_bug.cgi?id=4131)

---

### Post by Mr_Grieves on 2006-01-12
The freezing/halting bug affects (as far as I know) <0.9.3 and 0.9.5.

Wine 0.9.4 and Steam causes a crash to desktop, but this is patchable, read more here: [http://bugs.winehq.org/show_bug.cgi?id=4128](http://bugs.winehq.org/show_bug.cgi?id=4128)

I wonder if any users of other software than Wine are having the freezing issues with Steam?

To replicate the bug you just need to start Steam, not any game. After a minute or so Steam with freeze and become 100% unusable, then the freeze will release.. and so on.
About the freezing bug: [http://bugs.winehq.org/show_bug.cgi?id=4131](http://bugs.winehq.org/show_bug.cgi?id=4131)

---

### Post by Dark Damo on 2006-01-13
I'm getting the same problem and it looks exactly like this

[img]http://www.ubuntuforums.org/attachment.php?attachmentid=4438&d=1134413170[/img]

I know about the fonts but how can i transfer them over to my damn fonts thingy?

:(

---

### Post by Mr_Grieves on 2006-01-13
Download the font, then:

```

cp tahoma.ttf ~/.wine/drive_c/windows/fonts/

```

---

### Post by IsSuE on 2006-01-13
i got a prob with steam too.
i tried it with cedega, i installed several games, but when i run the game i get an steam error which tells me "steam validation rejected" .
my key is 100% valid and no one else is using it.

---

### Post by Dark Damo on 2006-01-13
> Download the font, then:

damo@OMG:~$ cp tahoma.ttf ~/.wine/drive_c/windows/fonts/
cp: cannot stat `tahoma.ttf': No such file or directory

---

### Post by Mr_Grieves on 2006-01-13
[QUOTE=IsSuE]i got a prob with steam too.
i tried it with cedega, i installed several games, but when i run the game i get an steam error which tells me "steam validation rejected" .
my key is 100% valid and no one else is using it.[/QUOTE]
Are you able to login? What happens if you run "Validate Steam/Game Cache" (right click on a game).

[QUOTE=Dark Damo]damo@OMG:~$ cp tahoma.ttf ~/.wine/drive_c/windows/fonts/
cp: cannot stat `tahoma.ttf': No such file or directory[/QUOTE]
Have you downloaded the font??? That command requires that you are in the same directory as the downloaded font.

---

### Post by Dark Damo on 2006-01-13
Where do i get the font from? BESIDES WINDOWS.

---

### Post by Mr_Grieves on 2006-01-13
[QUOTE=Dark Damo]Where do i get the font from? BESIDES WINDOWS.[/QUOTE]
The magical google fairy.

[http://www.google.com](http://www.google.com)

Want me to click for you? -Sarcasm- :p

Or perhaps a friend of yours can send it to you? Via e-mail? IRC? Etc.

---

### Post by IsSuE on 2006-01-14
strange thing, now i cant even run steam well. it locks up short after login.
i hate steam :/

---

### Post by Mustard on 2006-01-14
I haven't tried STEAM lately, but it was doing this lock up thing for me on Cedega as well.  I can only imagine its harder for someone using just wine to fix it.  On the Transgaming forums they were talking about it being a problem with a recent update of STEAM that broke third party projects like Cedega.  Some people get the problem and others don't.  I had it for a while, then it went away.  I would suggest trying at another time, as it might be something to do with some announcement that STEAM is trying to load up at login (thats my untested theory anyway),

---

### Post by Dark Damo on 2006-01-14
Why cant those Linux nazi's get there Arse into gear and make a Linux versionf FFS! 

It would make it easier for us and they would have a few more people using their  shit that they call software.

(I'm talking about steam not anyone who works on a linux or unix or freebsd of any kind)

I got the tahoma.ttf file. Where is my wine directory? i dont know how to navigate to it. :(

---

### Post by Mustard on 2006-01-14
[QUOTE=Dark Damo]Why cant those Linux nazi's get there Arse into gear and make a Linux versionf FFS! 

It would make it easier for us and they would have a few more people using their  shit that they call software.

(I'm talking about steam not anyone who works on a linux or unix or freebsd of any kind)

I got the tahoma.ttf file. Where is my wine directory? i dont know how to navigate to it. :([/QUOTE]

It's a hidden directory in your $HOME directory.  Press ctrl + H when you open up nautilus to show hidden files/folders and look for the .wine directory.

---

### Post by Dark Damo on 2006-01-14
Thank you i will try that now ;)

It works thank you very much!

Steam gives me this error

[img]http://img58.imageshack.us/img58/1836/steamerror5mr.jpg[/img]

---

### Post by Mr_Grieves on 2006-01-14
[QUOTE=Dark Damo]Thank you i will try that now ;)

It works thank you very much!

Steam gives me this error
[/QUOTE]
The base rule of getting things to work is. If something is missing, find it and put in .wine/ in it's corrisponding "Windows" folder. :)

In this case:

1) Download the DLL. [http://www.google.com](http://www.google.com) or other way.
2) Write this in a terminal:
```

cp /path/to/the_files_name ~/.wine/drive_c/windows/system

```
~ is always the path to your $HOME directory.

You will find alot of good information in my signature.

---

### Post by Mr_Grieves on 2006-01-14
[QUOTE=Mustard]I haven't tried STEAM lately, but it was doing this lock up thing for me on Cedega as well.  I can only imagine its harder for someone using just wine to fix it.  On the Transgaming forums they were talking about it being a problem with a recent update of STEAM that broke third party projects like Cedega.  Some people get the problem and others don't.  I had it for a while, then it went away.  I would suggest trying at another time, as it might be something to do with some announcement that STEAM is trying to load up at login (thats my untested theory anyway),[/QUOTE]
Steam and Counter-Strike 1.6/HL2 and Wine has been working flawlessly for me since Valves update between the 22th and 23rd of December.
Troubleshooting is being done for Wine at: [http://bugs.winehq.org/show_bug.cgi?id=4131](http://bugs.winehq.org/show_bug.cgi?id=4131)

We're at the moment waitng for info from Valve. I opened up a troubleticket with them.

---

### Post by Dark Damo on 2006-01-15
The dll is in the folder allready and it gives the error anyway. It didnt happen before i put the font in.

---

### Post by Mr_Grieves on 2006-01-15
[QUOTE=Dark Damo]The dll is in the folder allready and it gives the error anyway. It didnt happen before i put the font in.[/QUOTE]
That's because you came further in the loading of the game.
I recommend you search on you're error message on the web and winehq maillists.

---

### Post by fellowcanadian on 2006-02-26
> **Dark Damo]Thank you i will try that now  said:**
> http://img58.imageshack.us/img58/1836/steamerror5mr.jpg[/img]

I managed to find this on the steam forums:
[http://support.steampowered.com/cgi-bin/steampowered.cfg/php/enduser/std_adp.php?p_faqid=185&p_created=1093668755&p_sid=Ja4CY91i&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OTEmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1Db3VsZCBub3QgbG9hZCBtb2R1bGUgJ2Jpbi92Z3VpMi5kbGwn&p_li=&p_topview=1](http://support.steampowered.com/cgi-bin/steampowered.cfg/php/enduser/std_adp.php?p_faqid=185&p_created=1093668755&p_sid=Ja4CY91i&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OTEmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1Db3VsZCBub3QgbG9hZCBtb2R1bGUgJ2Jpbi92Z3VpMi5kbGwn&p_li=&p_topview=1)

---

### Post by abowman on 2006-02-26
I got steam to install using instructions from this site:
[http://www.stgraber.org/?p=6](http://www.stgraber.org/?p=6)

The only problem I'm having is low fps 15-30 in DOD and the game occassionally locking up.
I'm thinking it might have something to do with the audio settings in wine.  Right now I can only get DOD to run using oss.  I've tried using alsa, but DOD will only load as far as the splash screen and then freeze when the sound would ordinarily start.

---

### Post by Sandlst on 2006-02-27
@ Dark Damo-it gives me this error too, but only when I dont launch it from a terminal-did you try that?  I am having the same Fonts problem you did too, but I have Tahoma.ttf located in /.wine/drive_c/windows/fonts perhaps you have to put it somewhere else as well?  I noticed in the wineHQ guide to steam they have that 
"3. Install tahoma.ttf from either a windows installation, or download from the net. Installation will vary with flavor of linux." 
does this mean it also has to be installed somewhere else on the system?

*EDIT* cofirmed from linuX-gamers.net - 

"Steam requires the tahoma.ttf font. It is included in the Microsoft core fonts package. The package name depends on the distribution.  Alternatively google for tahoma.ttf, download it and put it into your X Server fonts directory. (usually /usr/X11/lib/X11/fonts/truetype)" apparently the core fonts package in the repos doesnt have tahoma, unless it puts it in a different place than the other fonts...

*EDIT* I was using Dapper and for many reasons decided to go back to Breezy for now....font problem fixed automagically.....I kept my home directories so tahoma.ttf was in /.wine/windows/fonts - not sure why it refused to work under Dapper

---

