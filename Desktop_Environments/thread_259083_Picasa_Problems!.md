---
title: "Picasa Problems!"
date: 2006-09-16
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-09-16
The linux package consists of wine and picasa,right?so i downloaded the windows version and installed it with wine 0.914.Now when i execute it,it gives me an error.
[email]pluto@Neptune:~/.wine[/email]/drive_c/Program Files/Picasa2$ wine Picasa2.exe
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
fixme:ole:CoResumeClassObjects stub
fixme:urlmon:DllGetClassObject {79eac9e5-baf9-11ce-8c82-00aa004ba90b}: no class found.
err:ole:get_inproc_class_object DllGetClassObject returned error 0x80040111
err:ole:create_server class {79eac9e5-baf9-11ce-8c82-00aa004ba90b} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {79eac9e5-baf9-11ce-8c82-00aa004ba90b} could be created for context 0x17
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
wine: Unhandled page fault on read access to 0x000001c0 at address 0x654d2c (thread 0009), starting debugger...
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x000001c0 in 32-bit code (0x00654d2c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00654d2c ESP:0033b738 EBP:0033bc24 EFLAGS:00010293(   - 00      RISA1C)
 EAX:00000000 EBX:00000070 ECX:00000000 EDX:019a6740
 ESI:00000003 EDI:00000005
Stack dump:
0x0033b738:  fffffffc 00000000 019a6740 00000000
0x0033b748:  019a6740 006558fa 00000000 00000000
0x0033b758:  0033b7cc 0033b7e8 ffffffff 019a6740
0x0033b768:  ffffffff 0033b96c 0033b954 009dd5e0
0x0033b778:  00000000 00000000 00000070 019a572d
0x0033b788:  009dd5e6 00000000 0000000b 00000004
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x00654d2c in picasa2 (+0x254d2c) (0x00654d2c)
  2 0x006560fc in picasa2 (+0x2560fc) (0x006560fc)
0x00654d2c: movl        0x0(%eax,%ebx,4),%eax
Modules:
Module  Address                 Debug info      Name (106 modules)
PE      370000-399000   Deferred        cdvdr.yti
PE      3a0000-3d7000   Deferred        ytitivo.yti
PE      400000-83e000   Export          picasa2
PE      b70000-c6a000   Deferred        expwebsites.yti
PE      10000000-10a43000       Deferred        picasai18n
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dea5000-7ded9000       Deferred        rsaenh<elf>
  \-PE  7deb0000-7ded9000       \               rsaenh
ELF     7ded9000-7dedd000       Deferred        libgpg-error.so.0
ELF     7dedd000-7df29000       Deferred        libgcrypt.so.11
ELF     7df29000-7df39000       Deferred        libtasn1.so.2
ELF     7df39000-7df66000       Deferred        libcrypt.so.1
ELF     7df73000-7dfdc000       Deferred        libgnutls.so.12
ELF     7dfdc000-7e009000       Deferred        libcups.so.2
ELF     7e03b000-7e06d000       Deferred        uxtheme<elf>
  \-PE  7e040000-7e06d000       \               uxtheme
ELF     7e06d000-7e082000       Deferred        midimap<elf>
  \-PE  7e070000-7e082000       \               midimap
PE      7e090000-7e09a000       --none--        msacm32
ELF     7e09a000-7e0d6000       Deferred        wineoss<elf>
  \-PE  7e0a0000-7e0d6000       \               wineoss
ELF     7e0d6000-7e0da000       Deferred        libxfixes.so.3
ELF     7e0da000-7e0e3000       Deferred        libxcursor.so.1
ELF     7e0e3000-7e0e6000       Deferred        libxrandr.so.2
ELF     7e0e6000-7e0ee000       Deferred        libxrender.so.1
ELF     7e0ee000-7e0f5000       Deferred        libdrm.so.2
ELF     7e0f5000-7e15b000       Deferred        libgl.so.1
ELF     7e15b000-7e1e5000       Deferred        winex11<elf>
  \-PE  7e170000-7e1e5000       \               winex11
ELF     7e1e5000-7e204000       Deferred        libexpat.so.1
ELF     7e204000-7e232000       Deferred        libfontconfig.so.1
ELF     7e232000-7e246000       Deferred        libz.so.1
ELF     7e246000-7e2af000       Deferred        libfreetype.so.6
ELF     7e2af000-7e2f9000       Deferred        crypt32<elf>
  \-PE  7e2c0000-7e2f9000       \               crypt32
ELF     7e2f9000-7e315000       Deferred        wintrust<elf>
  \-PE  7e300000-7e315000       \               wintrust
ELF     7e315000-7e3fb000       Deferred        libx11.so.6
ELF     7e3fb000-7e408000       Deferred        libxext.so.6
ELF     7e408000-7e420000       Deferred        libice.so.6
ELF     7e420000-7e46c000       Deferred        ddraw<elf>
  \-PE  7e430000-7e46c000       \               ddraw
ELF     7e46c000-7e488000       Deferred        imm32<elf>
  \-PE  7e470000-7e488000       \               imm32
ELF     7e488000-7e51b000       Deferred        oleaut32<elf>
  \-PE  7e4a0000-7e51b000       \               oleaut32
ELF     7e51b000-7e54a000       Deferred        winspool<elf>
  \-PE  7e520000-7e54a000       \               winspool
ELF     7e54a000-7e5e5000       Deferred        comdlg32<elf>
  \-PE  7e550000-7e5e5000       \               comdlg32
ELF     7e5e5000-7e617000       Deferred        urlmon<elf>
  \-PE  7e5f0000-7e617000       \               urlmon
ELF     7e617000-7e6fd000       Deferred        shell32<elf>
  \-PE  7e630000-7e6fd000       \               shell32
ELF     7e6fd000-7e753000       Deferred        shlwapi<elf>
  \-PE  7e710000-7e753000       \               shlwapi
ELF     7e753000-7e772000       Deferred        mpr<elf>
  \-PE  7e760000-7e772000       \               mpr
ELF     7e772000-7e7b9000       Deferred        wininet<elf>
  \-PE  7e780000-7e7b9000       \               wininet
ELF     7e7b9000-7e7e3000       Deferred        ws2_32<elf>
  \-PE  7e7c0000-7e7e3000       \               ws2_32
ELF     7e7e3000-7e7f6000       Deferred        libresolv.so.2
ELF     7e7f6000-7e815000       Deferred        iphlpapi<elf>
  \-PE  7e800000-7e815000       \               iphlpapi
ELF     7e815000-7e865000       Deferred        rpcrt4<elf>
  \-PE  7e820000-7e865000       \               rpcrt4
ELF     7e865000-7e8f6000       Deferred        ole32<elf>
  \-PE  7e870000-7e8f6000       \               ole32
ELF     7e8f6000-7e9b8000       Deferred        comctl32<elf>
  \-PE  7e900000-7e9b8000       \               comctl32
ELF     7e9b8000-7e9df000       Deferred        msvfw32<elf>
  \-PE  7e9c0000-7e9df000       \               msvfw32
ELF     7e9df000-7ea23000       Deferred        advapi32<elf>
  \-PE  7e9f0000-7ea23000       \               advapi32
ELF     7ea23000-7ea2d000       Deferred        libgcc_s.so.1
ELF     7eb02000-7ebb4000       Deferred        gdi32<elf>
  \-PE  7eb20000-7ebb4000       \               gdi32
ELF     7ebb4000-7ece6000       Deferred        user32<elf>
  \-PE  7ebd0000-7ece6000       \               user32
ELF     7ece6000-7ed6e000       Deferred        winmm<elf>
  \-PE  7ecf0000-7ed6e000       \               winmm
ELF     7ed6e000-7ed94000       Deferred        msacm32<elf>
ELF     7ed94000-7edcd000       Deferred        avifil32<elf>
  \-PE  7eda0000-7edcd000       \               avifil32
ELF     7edcd000-7ede1000       Deferred        lz32<elf>
  \-PE  7edd0000-7ede1000       \               lz32
ELF     7ede1000-7edfa000       Deferred        version<elf>
  \-PE  7edf0000-7edfa000       \               version
ELF     7ee2d000-7ef2f000       Deferred        kernel32<elf>
  \-PE  7ee50000-7ef2f000       \               kernel32
ELF     7ef2f000-7ef39000       Deferred        libnss_files.so.2
ELF     7ef39000-7ef42000       Deferred        libnss_nis.so.2
ELF     7ef42000-7ef57000       Deferred        libnsl.so.1
ELF     7ef57000-7ef60000       Deferred        libnss_compat.so.2
ELF     7ef60000-7ef82000       Deferred        libm.so.6
ELF     7ef82000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7d72000-b7d75000       Deferred        libxau.so.6
ELF     b7d77000-b7d7a000       Deferred        libdl.so.2
ELF     b7d7a000-b7ea9000       Deferred        libc.so.6
ELF     b7ea9000-b7ebb000       Deferred        libpthread.so.0
ELF     b7ebb000-b7ec0000       Deferred        libxxf86vm.so.1
ELF     b7ec0000-b7ec8000       Deferred        libsm.so.6
ELF     b7ec8000-b7fd9000       Deferred        libwine.so.1
ELF     b7fdc000-b7ff2000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c
        0000000d    0
00000008 (D) C:\Program Files\Picasa2\Picasa2.exe
        00000009    0 <==
Can anybody help?

---

### Post by catlett on 2006-09-16
I do not know if you prefer the windows version, but there is a linux version.
To install it you need to add the google repository first. Enter this command ```
sudo gedit /etc/apt/sources.list
```
Then add this line to the bottom
```
## Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free
```
Save the file and close. Now enter these 2 commands into the terminal
```
 sudo apt-get update
```
```
sudo apt-get install picasa
```
That is it. In my system, it is installed under Applications<Graphics<Picasa. If it doesn't show, enter this command to refresh your menu ```
update-menus
``` If you have any issues with linux google, here is there faq page. [http://picasa.google.com/linux/faq.html](http://picasa.google.com/linux/faq.html)

---

