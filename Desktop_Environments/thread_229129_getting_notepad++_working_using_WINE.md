---
title: "getting notepad++ working using WINE"
date: 2006-08-04
forum: Desktop Environments
---

### Post by soliac on 2006-08-04
Hi, I'm trying to get Notepad++ working in Dapper using Wine. I have got the latest version off the wine website, and have successfully installed Notepad++. But when I run "wine notepad++.exe" in the terminal I get an "unhandled page fault" and unhandled exception".
I'm rather new to Wine, but I have checked out the Wine App Database and it says that the latest version of Wine runs Notepad++ on Fedora, but an older version of Wine doesn't run it on Ubuntu. I tried changing some settings for the dll comctl32 as was said but it still didn't work.

Here is the error spat out when I try to run Notepad++. Is there an expert who could help?:confused: 

[email]luke@luke-laptop:~/.wine[/email]/drive_c/Program Files/Notepad++$ wine notepad++
wine: Unhandled page fault on read access to 0x00000020 at address 0x41a444 (thr ead 000d), starting debugger...
WineDbg starting on pid 0xc
Unhandled exception: page fault on read access to 0x00000020 in 32-bit code (0x0 041a444).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:0041a444 ESP:00328378 EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:0032d4d8 EBX:00000000 ECX:00000000 EDX:0032d5fc
 ESI:00000000 EDI:004c1be8
Stack dump:
0x00328378:  004c1be8 00000001 0032d4d8 00000000
0x00328388:  00000000 00000000 00000000 00000000
0x00328398:  00000000 0032d680 00000000 0032d5fc
0x003283a8:  00000000 00000000 00000000 00000000
0x003283b8:  00000000 00000000 00000000 00000000
0x003283c8:  00000000 00000000 7eba2790 00000000
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x0041a444 in notepad++ (+0x1a444) (0x0041a444)
0x0041a444: movl        0x20(%ebp),%eax
Modules:
Module  Address                 Debug info      Name (71 modules)
PE      400000-4b8000   Export          notepad++
PE      10000000-10051000       Deferred        scilexer
ELF     469f3000-46a09000       Deferred        ld-linux.so.2
ELF     46a67000-46a6c000       Deferred        libxxf86dga.so.1
ELF     46af5000-46afc000       Deferred        libdrm.so.2
ELF     46af5000-46afc000       Deferred        libdrm.so.2
ELF     46b25000-46b44000       Deferred        libexpat.so.1
ELF     46b46000-46b4e000       Deferred        libxrender.so.1
ELF     46b67000-46bcd000       Deferred        libgl.so.1
ELF     46beb000-46bee000       Deferred        libxrandr.so.2
ELF     46c38000-46c3c000       Deferred        libxfixes.so.3
ELF     46cc3000-46ccc000       Deferred        libxcursor.so.1
ELF     46faf000-46fc4000       Deferred        libnsl.so.1
ELF     46fc6000-4702f000       Deferred        libgnutls.so.12
ELF     47031000-4707d000       Deferred        libgcrypt.so.11
ELF     4707f000-4708f000       Deferred        libtasn1.so.2
ELF     47091000-47095000       Deferred        libgpg-error.so.0
ELF     47282000-473b1000       Deferred        libc.so.6
ELF     473b3000-473b6000       Deferred        libdl.so.2
ELF     473b8000-473da000       Deferred        libm.so.6
ELF     473dc000-473f0000       Deferred        libz.so.1
ELF     473f2000-474d8000       Deferred        libx11.so.6
ELF     474da000-474dd000       Deferred        libxau.so.6
ELF     474df000-474ec000       Deferred        libxext.so.6
ELF     474ee000-47500000       Deferred        libpthread.so.0
ELF     47502000-4756b000       Deferred        libfreetype.so.6
ELF     4756d000-47585000       Deferred        libice.so.6
ELF     47587000-4758f000       Deferred        libsm.so.6
ELF     4776f000-47779000       Deferred        libgcc_s.so.1
ELF     47862000-4788f000       Deferred        libcrypt.so.1
ELF     47a13000-47a40000       Deferred        libcups.so.2
ELF     47a13000-47a40000       Deferred        libcups.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e1f8000-7e259000       Deferred        msvcrt<elf>
  \-PE  7e210000-7e259000       \               msvcrt
ELF     7e400000-7e431000       Deferred        uxtheme<elf>
  \-PE  7e410000-7e431000       \               uxtheme
ELF     7e440000-7e45c000       Deferred        imm32<elf>
  \-PE  7e450000-7e45c000       \               imm32
ELF     7e5e6000-7e669000       Deferred        winex11<elf>
  \-PE  7e600000-7e669000       \               winex11
ELF     7e733000-7e762000       Deferred        winspool<elf>
  \-PE  7e740000-7e762000       \               winspool
ELF     7e762000-7e7fd000       Deferred        comdlg32<elf>
  \-PE  7e770000-7e7fd000       \               comdlg32
ELF     7e7fd000-7e8db000       Deferred        shell32<elf>
  \-PE  7e810000-7e8db000       \               shell32
ELF     7e8db000-7e8fa000       Deferred        iphlpapi<elf>
  \-PE  7e8e0000-7e8fa000       \               iphlpapi
ELF     7e8fa000-7e949000       Deferred        rpcrt4<elf>
  \-PE  7e910000-7e949000       \               rpcrt4
ELF     7e949000-7e9da000       Deferred        ole32<elf>
  \-PE  7e960000-7e9da000       \               ole32
ELF     7e9da000-7ea30000       Deferred        shlwapi<elf>
  \-PE  7e9f0000-7ea30000       \               shlwapi
ELF     7ea30000-7ea73000       Deferred        advapi32<elf>
  \-PE  7ea40000-7ea73000       \               advapi32
ELF     7eb55000-7ec07000       Deferred        gdi32<elf>
  \-PE  7eb70000-7ec07000       \               gdi32
ELF     7ec07000-7ed39000       Deferred        user32<elf>
  \-PE  7ec20000-7ed39000       \               user32
ELF     7ed39000-7edfb000       Deferred        comctl32<elf>
  \-PE  7ed40000-7edfb000       \               comctl32
ELF     7ee2e000-7ef2f000       Deferred        kernel32<elf>
  \-PE  7ee50000-7ef2f000       \               kernel32
ELF     7ef2f000-7ef39000       Deferred        libnss_files.so.2
ELF     7ef39000-7ef42000       Deferred        libnss_nis.so.2
ELF     7ef57000-7ef60000       Deferred        libnss_compat.so.2
ELF     7ef82000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7e64000-b7f74000       Deferred        libwine.so.1
Threads:
process  tid      prio (all id:s are in hex)
0000000e
        0000000f    0
0000000c (D) C:\Program Files\Notepad++\notepad++.exe
        0000000d    0 <==

---

### Post by patrickfromspain on 2006-08-04
I know it's not the solution, but maybe you could try Crimson editor, which also has great features. I got it to work with crossover office.

EDIT: tried Notepad++ in Crossover and it happens the same as in wine

---

### Post by PaulMellors on 2006-08-04
I know it doesn't answer your question, but why?  It's far easier to install bluefish or some other similar app, i still can't understand why people who run linux still want to run windowz apps...no offence matey.

---

### Post by soliac on 2006-08-04
Hey all,
The reason I want Notepad++ is mostly because of its large feature set, that and because I can't find any other editor that lets you have two tabs open side by side in the same window.

---

### Post by Lord Illidan on 2006-08-04
Kate is good.

---

### Post by llamakc on 2006-08-04
Emacs does screen splitting also.

---

### Post by altonbr on 2006-11-08
What about [Scribes]("http://scribes.sourceforge.net/"), [jEdit]("http://jedit.org/") or [Eclipse]("http://www.eclipse.org/")?

---

### Post by altonbr on 2006-11-11
Actually.. now that I tried those programs, [SCREEM]("http://www.screem.org/") and [BlueFish]("http://bluefish.openoffice.nl/index.html"), I really miss Notepad++. ALOT.

I'll stick with gEdit for now.

---

### Post by 5of0 on 2007-07-16
I totally understand why Notepad++ is so valuable...I tried bluefish, only to find out is only for HTML?  What the crap?  I use Notepad++ because I can use it for HTML, PHP, C++, Javascript, Perl, whatever I'm using at the moment.  I'm sorry, but putting up Bluefish as an alternative to Notepad++ is like...putting up a single blade as a viable alternative for a swiss army knife.  Sure, the average person may just use the knife, but I actually use the screwdriver/corkscrew/tweezers/etc.  Bluefish may be fine for people who only code in HTML, but for the rest of us, Notepad++ is a godsend.  And I agree, gEdit is better than BlueFish - it's more like one of those little multi-function knives - pretty useful, but just not as good as the full blown deal :)

That said, I got Notepad++ working first try with the current Wine on Feisty Fawn - have you tried it recently?  There's even a howto on the notepad++ site here:
[http://notepad-plus.sourceforge.net/uk/nppLinux.php](http://notepad-plus.sourceforge.net/uk/nppLinux.php)

---

