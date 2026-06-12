---
title: "i need nooby help for wine"
date: 2006-07-20
forum: Gaming &amp; Leisure
---

### Post by timofthec on 2006-07-20
ok - i followed a great howto by gazj on how to install and set wine up and as far as i can tell, its all loaded and waiting to go.

however, the thing i cant work out is how to use it to install and run windows programmes.

to explain, i have an old windows game that i want to install and run under ubuntu.  problem is, i don't have a clue as to how to load the game under ubuntu using wine.  do i have to have wine open and use it to install the game or will the normal windows loader install the game and i just run it through wine?

any help or links to how to do it that i haven't found yet would be great.

---

### Post by doomstone on 2006-07-20
Open a terminal and type
```
wine /path-to-game/somefile.exe
```

and the game will start

---

### Post by timofthec on 2006-07-20
> **doomstone said:**
> Open a terminal and type
```
wine /path-to-game/somefile.exe
```

and the game will start

thnx doom.

is that how i install the game as well or is that just the command to get the game running once its installed?

---

### Post by Lord Illidan on 2006-07-20
You can run the installer through wine as well. What is the name of the game?

---

### Post by timofthec on 2006-07-21
Sorry lord - went to sleep 8) 

The game - my most fav game - is called M.A.X (Mechanised Assault and Exploration).  It’s an old win95 game that they squeezed into win98.

There are also a few other programmes that I want to start using under ubuntu, I just need to work out how and wine seems the best option.  I'm aware of cedega but am reluctant to put me hand in me pocket till I'm sure its the way to go.

If there is a howto or guide I can follow just let me know, I've had a search but haven’t found anything yet - there’s an awful of info in these forums

---

### Post by timofthec on 2006-07-21
As an update - I've been poking around on the Winehq IRC chat and was told that I need to enter "wine /whatever/setup.exe".  I was told that the "whatever" is the path to where the "setup.exe" file is located.  Not been able to get a great response but this is fine and I understand what I'm being told to do, however, the thing that I'm struggling with is do I use this same string to install the game as well?

I.e. if I were to type "wine /D:/Setup.exe" would wine install the game for me?  If so, would I then just type wine /thepathwherethgamewasinstalled/game.exe to have the game run through wine?


I've looked through the wine documentation and can see how things can be run using wine but I can't work out how to install them first.  Any help would be welcome as always

---

### Post by tonyp1969 on 2006-07-21
wine /media/cdrom/setup.exe

---

### Post by Lord Illidan on 2006-07-21
Was sleeping also!

What is the link to your CD ROM drive under Linux.

If it is /media/cdrom, then run wine /media/cdrom/setup.exe

To check where your cdrom is mounted, give us your /etc/fstab file (paste it here), and we'll tell you where.

---

### Post by timofthec on 2006-07-21
right Lord, the contents of the etc/fstab file are : -

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I have also attempted to get the game to install by putting the disk in the cd drive and using the terminal to run "wine /media/cdrom0/install.exe"

this is the output that i get from that: -
chambos@chambos-desktop:~$ wine /media/cdrom0/install.exe
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
wine: Unhandled page fault on read access to 0x00001bb0 at address 0x7ffc41d3 (thread 000a), starting debugger...
WineDbg starting on pid 0x8
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image D:\install.exe
Unhandled exception: page fault on read access to 0x00001bb0 in 32-bit code (0x7ffc41d3).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:11b7 GS:0033
 EIP:7ffc41d3 ESP:7e9a95f0 EBP:7e9a9608 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7ffd41b0 ECX:7e9a985c EDX:7e9a96e4
 ESI:7e9a985c EDI:7e9a96e4
Stack dump:
0x7e9a95f0:  00001bb7 7ffb8dd7 7e9a985c 7ffd41b0
0x7e9a9600:  00000001 7e9a985c 7e9a9740 7ffb9c96
0x7e9a9610:  7e9a96e4 7e9a985c 7e9a9620 7e9a96e4
0x7e9a9620:  0000ffea 00000000 000003da 0000064e
0x7e9a9630:  000038ad 0000ff04 00000000 00000000
0x7e9a9640:  00000000 00000000 00000000 ffffffff
0236: sel=11b7 base=7fe4c000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ffc41d3 in ntdll (+0x441d3) (0x7ffc41d3)
  2 0x7ffb9c96 __wine_enter_vm86+0x116 in ntdll (0x7ffb9c96)
  3 0x7fc93401 K32WOWCallback16Ex+0x291 in kernel32 (0x7fc93401)
  4 0x7ebeb1c1 DOSVM_Enter+0xd1 in winedos (0x7ebeb1c1)
  5 0x7ec06654 in winedos (+0x26654) (0x7ec06654)
  6 0x7fc879c7 in kernel32 (+0x679c7) (0x7fc879c7)
  7 0x7ffbd83f in ntdll (+0x3d83f) (0x7ffbd83f)
  8 0xb7f79341 start_thread+0x81 in libpthread.so.0 (0xb7f79341)
  9 0xb7f0e4ee __clone+0x5e in libc.so.6 (0xb7f0e4ee)
0x7ffc41d3: pop %es
Modules:
Module  Address                 Debug info      Name (57 modules)
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e9ab000-7e9c0000     Deferred        midimap<elf>
  \-PE  0x7e9b0000-7e9c0000     \               midimap
ELF     0x7ead5000-7eaf7000     Deferred        msacm32<elf>
  \-PE  0x7eae0000-7eaf7000     \               msacm32
ELF     0x7eaf7000-7eb0e000     Deferred        msacm<elf>
  \-PE  0x7eb00000-7eb0e000     \               msacm
ELF     0x7eb0e000-7eb50000     Deferred        wineoss<elf>
  \-PE  0x7eb20000-7eb50000     \               wineoss
ELF     0x7eb50000-7ebd1000     Deferred        winmm<elf>
  \-PE  0x7eb60000-7ebd1000     \               winmm
ELF     0x7ebd1000-7ec2e000     Export          winedos<elf>
  \-PE  0x7ebe0000-7ec2e000     \               winedos
ELF     0x7ec72000-7ec76000     Deferred        libxfixes.so.3
ELF     0x7ec76000-7ec7f000     Deferred        libxcursor.so.1
ELF     0x7ec7f000-7ec87000     Deferred        libxrender.so.1
ELF     0x7ec87000-7eca2000     Deferred        imm32<elf>
  \-PE  0x7ec90000-7eca2000     \               imm32
ELF     0x7eca2000-7ed08000     Deferred        libgl.so.1
ELF     0x7ed08000-7edee000     Deferred        libx11.so.6
ELF     0x7edee000-7edfb000     Deferred        libxext.so.6
ELF     0x7edfb000-7ee13000     Deferred        libice.so.6
ELF     0x7ee13000-7ee90000     Deferred        winex11<elf>
  \-PE  0x7ee20000-7ee90000     \               winex11
ELF     0x7ee90000-7eeaf000     Deferred        libexpat.so.1
ELF     0x7eeaf000-7eedd000     Deferred        libfontconfig.so.1
ELF     0x7eedd000-7eee4000     Deferred        libdrm.so.2
ELF     0x7eee4000-7eee9000     Deferred        libxxf86vm.so.1
ELF     0x7eee9000-7eefd000     Deferred        libz.so.1
ELF     0x7eefd000-7ef66000     Deferred        libfreetype.so.6
ELF     0x7ef66000-7efa2000     Deferred        advapi32<elf>
  \-PE  0x7ef70000-7efa2000     \               advapi32
ELF     0x7f077000-7f977000     Deferred        gdi32<elf>
  \-PE  0x7f0c0000-7f977000     \               gdi32
ELF     0x7f977000-7fa90000     Deferred        user32<elf>
  \-PE  0x7f990000-7fa90000     \               user32
ELF     0x7fba3000-7fbab000     Deferred        libsm.so.6
ELF     0x7fbab000-7fbc0000     Deferred        winevdm<elf>
  \-PE  0x7fbb0000-7fbc0000     \               install
ELF     0x7fbc2000-7fbc7000     Deferred        libxxf86dga.so.1
ELF     0x7fbc7000-7fbd1000     Deferred        libgcc_s.so.1
ELF     0x7fc04000-7fd00000     Export          kernel32<elf>
  \-PE  0x7fc20000-7fd00000     \               kernel32
ELF     0x7fe10000-7fe13000     Deferred        libxau.so.6
ELF     0x7fe13000-7fe1d000     Deferred        libnss_files.so.2
ELF     0x7fe1d000-7fe26000     Deferred        libnss_nis.so.2
ELF     0x7fe26000-7fe3b000     Deferred        libnsl.so.1
ELF     0x7fe3b000-7fe44000     Deferred        libnss_compat.so.2
ELF     0x7fe53000-7fe75000     Deferred        libm.so.6
ELF     0x7fe75000-7ff6c000     Deferred        libwine_unicode.so.1
ELF     0x7ff6c000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e42000-b7e45000     Deferred        libdl.so.2
ELF     0xb7e45000-b7f74000     Export          libc.so.6
ELF     0xb7f74000-b7f86000     Export          libpthread.so.0
ELF     0xb7f86000-b7fa0000     Deferred        libwine.so.1
ELF     0xb7faf000-b7fc5000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\install.exe
        0000000a    0 <==
        00000009    0
WineDbg terminated on pid 0x8

not sure if this means anything to anybody.

As advised by the winehq irc channel I have also tried running "winecfg" and  adding the file manually - however, this does nothing.

Oh - i also tried right clicking the install.exe file on the cdrom and selecting "open with wine windows emulator" but again nothing, although it does cause the cdrom drive to spin up.

I'm sure I'm just being a noob and need some hand holding to get this working.

Please hold my hand ;)

---

### Post by warbread on 2006-07-21
> **timofthec said:**
> 
As advised by the winehq irc channel I have also tried running "winecfg" and  adding the file manually - however, this does nothing.


By this do you mean you asked WineCFG to autodetect your drives?  If not, that's a good next step.  Type in 'sudo winecfg' into the terminal, enter your password and click on the "Drives" tab when winecfg comes up.  Click on the auto-detect button.  Click 'Apply' then 'OK'.

---

### Post by timofthec on 2006-07-22
> **warbread said:**
> By this do you mean you asked WineCFG to autodetect your drives?  If not, that's a good next step.  Type in 'sudo winecfg' into the terminal, enter your password and click on the "Drives" tab when winecfg comes up.  Click on the auto-detect button.  Click 'Apply' then 'OK'.

Ok, tried this and I get a couple of lines of erroirs in the Terminal re: -desktop:~$ sudo winecfg
Password:
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0

Under the Drives tab in Wine there is a list of 7 drives under Drive mapping 
c: ../drive_c
d: /media/cdrom0
e: /media/hda1
f: /home/USER/winetools
g: /media/hda5
h: /home/USER
z: /

---

### Post by jincast90 on 2006-07-22
> **timofthec said:**
> ok - i followed a great howto by gazj on how to install and set wine up and as far as i can tell, its all loaded and waiting to go.

however, the thing i cant work out is how to use it to install and run windows programmes.

to explain, i have an old windows game that i want to install and run under ubuntu.  problem is, i don't have a clue as to how to load the game under ubuntu using wine.  do i have to have wine open and use it to install the game or will the normal windows loader install the game and i just run it through wine?

any help or links to how to do it that i haven't found yet would be great.

You used a guide? I just installed it through the package manager. Workes like a charm.

---

### Post by timofthec on 2006-07-23
hmm, maybe I needd to do it that way to get it to work then.

Anybody out there know how to uninstall wine and all of the programmes that I downloaded into it?  Or can I just reload it through packet manager?

---

