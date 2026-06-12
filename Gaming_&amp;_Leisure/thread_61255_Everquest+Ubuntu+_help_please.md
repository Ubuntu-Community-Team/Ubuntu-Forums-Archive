---
title: "Everquest+Ubuntu+??? help please"
date: 2005-08-31
forum: Gaming &amp; Leisure
---

### Post by Phreekystylze on 2005-08-31
I have been trying for 3 days straight now to install Everquest on Ubuntu.
Things I have tried...

Wine
WineX
Cedega
CedegaCVS - linux-gamers.net
CVSWine - linux-gamers.net
CVSwineX - linux-gamers.net
Wine - Latest from Synaptic

all with verying success, I actually got the game to install but not even make it to the EULA with wine

with any version of cedega I can not get the game to install from the discs or from copying the CD's to the HDD (m not able to swap disks for the install - I did try the -monitor-cdrom-eject, no dice), I can copy the game files from my windows machine to the Trans Gaming drive on my Ubuntu and when I do "cedega EverQuest.exe", it will go through the patcher and make it all the way to Server select screen, after chosing server, it will crash 100% of the time. ](*,) 

AMD Athlon XP 2100
512 PC3200
nVidia GeForce FX 5500 - Drivers - nVidia's 7667 release

I am really liking Ubuntu, and to be honest, this is all I need to get running to keep me from leaving windows on my other machines, any help would be great, and much appreciated.

Thanks in advance for the help.
Phreekystylze

p.s.
I am 3 new to Ubuntu, used to mess with RH back in the 7.1 days, been about 2 years since I messed with linux at all, reason..? not being able to get Everquest to install and run  :| so please be kind in your replies, thanks!

---

### Post by Perfect Storm on 2005-08-31
What the users rated Everquest [http://transgaming.org/gamesdb/games/view.mhtml?game_id=2325](http://transgaming.org/gamesdb/games/view.mhtml?game_id=2325)
But it's with the pay version of Cedega + Point2Play. Perhaps you should give it a try. It's $15 for 3 month, then $5 every month after. You can allways cancel after the 3 month, but then you can't update cedega and Point2Play anymore. And yes, there's a diffrent from the pay version to the free version.
Also check Cedega Everquest forum for guidance and help.

---

### Post by blueturtl on 2005-08-31
> with any version of cedega I can not get the game to install from the discs or from copying the CD's to the HDD (m not able to swap disks for the install 

Actually, there may be a way around this. I had the same problem installing NOLF on Ubuntu with Cedega and I just couldn't get the disc to unmount while the installation process was running to insert disc 2 so here's what I did:

I simply stubbornly copied the files to my desktop from the second CD.
When I started the installation from the first disc and it told me to insert disc 2 I simply forwarded the installer to my desktop directory. It happily installed the files from there, and then went on to finish the installation.

If the Everquest installer doesn't allow you to point to a file path I'm not sure this will help though, but if you can, give it a try!

---

### Post by KingBahamut on 2005-08-31
For Disc mounting problems, you can create ISOs out of the CDs , then mount the ISOs locally to correct this issue. I had to do it on a friends machine with UT2004. 

mount -o loop -t iso9660 file.iso /<mountpoint> 

thats about the easiest way to address the mounting issue, and it totally circumvents the hardware problem of an ejecting CD.

---

### Post by Phreekystylze on 2005-08-31
[QUOTE=blueturtl]
I simply stubbornly copied the files to my desktop from the second CD.
When I started the installation from the first disc and it told me to insert disc 2 I simply forwarded the installer to my desktop directory. It happily installed the files from there, and then went on to finish the installation.

If the Everquest installer doesn't allow you to point to a file path I'm not sure this will help though, but if you can, give it a try![/QUOTE]
Thanks, did try this, as I stated in the first post   :)  however when it got to the last disk of the install it want Disk 1 again, to which I was not able to point to  :( 


> mount -o loop -t iso9660 file.iso /<mountpoint> 
I will give this a try after I get the sleep out of my eyes, Thanks guys.

just an FYI, I did try the Pay Cedega, with no success

-Phreekystylze

---

### Post by Phreekystylze on 2005-08-31
Thanks for all the help guys, however I am still in the same boat, No Everquest

I did try  "mount -o loop -t iso9660 file.iso /<mountpoint>", and the install started, however when it came time to change disks I was not able to umount this, Kept getting a "the device is busy" error.

So I am still hoping, and still trying new things, if anyone has any input for this, other then sending me to to nearly non existant support forums for TransGaming, I would be most appreciative.

If anyone has installed EverQuest on Ubuntu 5.04 and has it running, could you PLEASE post how you did it? I am at my wits end here

Thanks,
-Phreek

---

### Post by blueturtl on 2005-08-31
> Thanks, did try this, as I stated in the first post  however when it got to the last disk of the install it want Disk 1 again, to which I was not able to point to 

Did you copy disc 2 content to HD *before* starting the installation from disc 1?

The NOLF installer has the same nasty habit: you start with disc 1, then it asks for disc 2 and after that disc 1 AGAIN.

This is what I did:

1st I inserted disc 2 and copied it's files to my desktop.

I then removed disc 2 and replaced it with disc 1 (before starting the game installer).

I then run the installer.

When it asks for disc 2 I just tell it to look in my desktop folder *without removing disc 1 from the drive!*

When it asks for disc 1 again I just point it back to the mounted disc still in the drive.

It might be possible that I've misunderstood you.
Maybe the installer doesn't let you search for the directory manually?
Some installers do also actually look for the disc by label rather than the files.

---

### Post by Phreekystylze on 2005-08-31
It does let me search manually, however it seems that it is never really "looking" for the disk/directory after I point it, it errors and says, Unable to find file in specified location, please insert disk 2 and press ok"

no matter if it is a CD or a disk

I copied all 4 disks to my hdd, in their own folders under the same directory, the installer will auto find them, however at the end of the last disk, it asks for disk 1 again, at which point, even with disk one in the cdrom and mounted, it will not locate it, same scenario if I point it back to the cd1 directory where disk one is. ](*,) 

-Phreek

---

### Post by Phreekystylze on 2005-08-31
blueturtl are you installing with Cedega or another program?

-Phreek

---

### Post by blueturtl on 2005-08-31
> It does let me search manually, however it seems that it is never really "looking" for the disk/directory after I point it, it errors and says, Unable to find file in specified location, please insert disk 2 and press ok"

Maybe it's a bug? I had a similar experience installing Unreal. I have a separate volume that I install games on, so the game didn't go into the default C:\Unreal. The install went fine, but when I tried to run the game it said it couldn't find the file/directory. I checked many times and the directory was correct. TransGaming support then suggested I install the game in the default directory and it ran perfectly ever since. I still have no idea what might have caused the game not to run or be found when the path was obviously correct, could be an inner quirk of WINE.

> blueturtl are you installing with Cedega or another program?

I use Cedega official 4.4.1 to install and run Windows games.

---

### Post by Phreekystylze on 2005-08-31
Thanks a ton Blueturtl, I guess I wil go ahead and reactivate my TransGaming account and get a fresh copy...my current is 4.2.x

Was kinda hoping to game "open source" lol, you know, without paying TG more money.

tried the cvs of it, and that has no install shield support/cd protection stuff in it.

Thanks again Blue, will let ya know how it goes

-Phreek

---

### Post by Phreekystylze on 2005-08-31
Thanks a ton Blueturtl, I guess I wil go ahead and reactivate my TransGaming account and get a fresh copy...my current is 4.2.x

Was kinda hoping to game "open source" lol, you know, without paying TG more money.

tried the cvs of it, and that has no install shield support/cd protection stuff in it.

Thanks again Blue, will let ya know how it goes.

oh yeah, and are you using point2play? or just cedega /media/cdrom0/install.exe ?

-Phreek

---

### Post by blueturtl on 2005-08-31
> Thanks a ton Blueturtl, I guess I wil go ahead and reactivate my TransGaming account and get a fresh copy...my current is 4.2.x

Don't mention it. I hope it's a worthy investment. At least you'll be entitled to bug the TransGaming staff with this if it still doesn't work, eh?  ;-)

> oh yeah, and are you using point2play?

Yup. Latest version.

Just make sure you've tried every silly thing before shelling out more money ok? It doesn't even have to make sence... Most of the quirks I've encountered have been really simple to fix, *after you know what you have to do...*  :mad:

---

### Post by Phreekystylze on 2005-08-31
lol, will do

decided to give it one or two more days fiddling with it....
I tried once again with the latest wine...and needless to say...it ran through all 4 disks and installed the game...yet would not play it  :mad: 

-Phreek

---

### Post by Phreekystylze on 2005-09-02
One last question Blue....what video card are you running?

-Phreek

---

### Post by Phreekystylze on 2005-09-03
I have noticed this has gotten a few hits, so I will post my progress here...

I am now able to load the game up with "cedega EverQuest.exe" however, after selecting my server, it crashes.

Any thoughts? anyone??

Thanks,
-Phreek

---

### Post by oneybm on 2005-09-03
I no longer play Everquest; however, when I first started messing with Ubuntu I did and the way I got it to work was to copy my entire EQ installation fromt he Windows install that I had on my hard drive.  It took forever to get all 2 gbs across but once I did that I got it to load, hit server select, character select and even get in the game.  It was really laggy and the graphics were pretty messed up but at least it worked.

If you still have your Windows install of Linux available I would definetly suggest doing that.

Hope it helps,

---

### Post by blueturtl on 2005-09-03
> One last question Blue....what video card are you running?

I've got a GeForce4 Ti4200 (a Gainward PowerPack Ti4200 Golden Sample with 128 megs of RAM and enhanced clock frequencies). It's starting to be an old card, but for what it's worth it still  runs many games (most of what I have) with nice framerates, including Half-Life 2. Having an nVidia card is a bliss for a Linux user.  ;-) 

> I no longer play Everquest; however, when I first started messing with Ubuntu I did and the way I got it to work was to copy my entire EQ installation fromt he Windows install that I had on my hard drive. It took forever to get all 2 gbs across but once I did that I got it to load, hit server select, character select and even get in the game. It was really laggy and the graphics were pretty messed up but at least it worked.

The buggy graphics and laggyness might be caused in this case by the fact the game has detected the video and audio hardware used in the system it was initially installed on. Then after you move it to an alternate computer and say the graphics card is different, the settings that were once ok become obsolete. This is just speculation though as I've got no experience of the game in question.

> I am now able to load the game up with "cedega EverQuest.exe" however, after selecting my server, it crashes.

Any thoughts? anyone??

I'm sorry but since I don't own a copy of the game I can't really help with testing or anything.  :| Does it return an error?

---

### Post by Phreekystylze on 2005-09-05
I will post the error that is dumped to the terminal when I get Ubuntu reinstalled, been tyring a few other distro's with the same issue.

as a side note, when it dumps, when going to character select, this is the first place it actually has to load 3d graphics, I suspect something with dx9 not working right, as everquest requires dx9 now.

-Phreek

---

### Post by Phreekystylze on 2005-09-06
ok, here is the error....it is alot....

```
wine: Unhandled exception, starting debugger...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0xb7ff7195
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0xb7ee8000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0xb7ed3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0xb7e0b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0xb7e09000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0xb7ddf000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0xb7cb2000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0xb7ca2000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0xb7c9f000)
No debug information in ELF '/lib/ld-linux.so.2' (0xb7feb000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32.so' (0xb778f000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so' (0xb7667000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so' (0xb75f0000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32.so' (0xb75c9000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinmm.so' (0xb7573000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwsock32.so' (0xb7566000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libws2_32.so' (0xb754e000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libiphlpapi.so' (0xb753f000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libdinput8.so' (0xb753a000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libdinput.so' (0xb7516000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libddraw.so' (0xb74d2000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_tsx11.so' (0xb74c0000)
No debug information in ELF '/usr/X11R6/lib/libSM.so.6' (0xb74ae000)
No debug information in ELF '/usr/X11R6/lib/libICE.so.6' (0xb7496000)
No debug information in ELF '/usr/lib/libGL.so.1' (0xb7417000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libGLU.so.1' (0xb735c000)
No debug information in ELF '/usr/X11R6/lib/libXext.so.6' (0xb734f000)
No debug information in ELF '/usr/X11R6/lib/libX11.so.6' (0xb728a000)
No debug information in ELF '/usr/lib/libGLcore.so.1' (0xb6b21000)
No debug information in ELF '/usr/lib/tls/libnvidia-tls.so.1' (0xb6b1f000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libimm32.so' (0xb6ab5000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libversion.so' (0xb6a97000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/liblz32.so' (0xb6a90000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libole32.so' (0xb6a2b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/librpcrt4.so' (0xb69e5000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshell32.so' (0xb696a000)
No debug information in ELF '/usr/lib/libpng.so.3' (0xb693d000)
No debug information in ELF '/usr/lib/libz.so.1' (0xb692c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshlwapi.so' (0xb68ec000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomctl32.so' (0xb6866000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineserver.so' (0xb6825000)
No debug information in ELF '/usr/lib/libfreetype.so.6' (0xb67af000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libx11drv.so' (0xb6731000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2' (0xb672f000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2' (0xb6713000)
No debug information in ELF '/usr/lib/libXcursor.so.1' (0xb6701000)
No debug information in ELF '/usr/lib/libXrender.so.1' (0xb66f9000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineoss.drv.so' (0xb6597000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm32.so' (0xb6585000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinemp3.acm.so' (0xb6441000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libimaadp32.acm.so' (0xb643b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsg711.acm.so' (0xb6435000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm.drv.so' (0xb642d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmidimap.drv.so' (0xb6427000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libd3dgl.so' (0xb5d98000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libd3d9.so' (0xb4364000)
No debug information in ELF '/lib/tls/i686/cmov/libnss_files.so.2' (0xb3fb7000)
No debug information in ELF '/lib/tls/i686/cmov/libnss_dns.so.2' (0xb40d3000)
No debug information in ELF '/lib/tls/i686/cmov/libresolv.so.2' (0xaee6a000)
No debug information in 32bit DLL 'C:\Program Files\Sony\EverQuest Trilogy\eqgame.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0xb7f25000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0xb77c2000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0xb75db000)
No debug information in 32bit DLL 'GDI32.DLL' (0xb760f000)
No debug information in 32bit DLL 'USER32.DLL' (0xb769e000)
No debug information in 32bit DLL 'WINMM.DLL' (0xb7581000)
No debug information in 32bit DLL 'C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\MSS32.DLL' (0x21100000)
No debug information in 32bit DLL 'IPHLPAPI.DLL' (0xb7546000)
No debug information in 32bit DLL 'WS2_32.DLL' (0xb7556000)
No debug information in 32bit DLL 'WSOCK32.DLL' (0xb756a000)
No debug information in 32bit DLL 'DDRAW.DLL' (0xb74e8000)
No debug information in 32bit DLL 'DINPUT.DLL' (0xb7523000)
No debug information in 32bit DLL 'DINPUT8.DLL' (0xb753c000)
No debug information in 32bit DLL 'IMM32.DLL' (0xb6abb000)
No debug information in 32bit DLL 'LZ32.DLL' (0xb6a93000)
No debug information in 32bit DLL 'VERSION.DLL' (0xb6a9a000)
No debug information in 32bit DLL 'RPCRT4.DLL' (0xb6a08000)
No debug information in 32bit DLL 'OLE32.DLL' (0xb6a4a000)
No debug information in 32bit DLL 'C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\DSETUP.DLL' (0xb6aa1000)
No debug information in 32bit DLL 'SHLWAPI.DLL' (0xb6909000)
No debug information in 32bit DLL 'COMCTL32.DLL' (0xb6874000)
No debug information in 32bit DLL 'SHELL32.DLL' (0xb6990000)
No debug information in 32bit DLL 'X11DRV.DLL' (0xb674f000)
No debug information in 32bit DLL 'MSACM32.DLL' (0xb658a000)
No debug information in 32bit DLL 'WINEOSS.DRV' (0xb659a000)
No debug information in 32bit DLL 'MSACM.DRV' (0xb6430000)
No debug information in 32bit DLL 'MIDIMAP.DRV' (0xb6429000)
No debug information in 32bit DLL 'D3DGL.DLL' (0xb5da9000)
No debug information in 32bit DLL 'D3D9.DLL' (0xb4374000)
No debug information in 32bit DLL 'C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\DPVS.DLL' (0xb4315000)
No debug information in 32bit DLL 'C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\EQGRAPHICSDX9.DLL' (0x10000000)
Unhandled exception: page fault on read access to 0x4d9cdf1f in 32-bit code (0x100e2c52).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:100e2c52 ESP:b7a21f78 EBP:b7a21f88 EFLAGS:00210a87(  R- 00O I S - -P1C)
 EAX:4d9cdf1f EBX:b2633f34 ECX:b2632630 EDX:4d9cdf1f
 ESI:b2632630 EDI:b2632610
Stack dump:
0xb7a21f78 (KERNEL32.DLL.wine_get_unix_file_name+0x21eb20):  b2632630 101a252c 101a2549 00000012
0xb7a21f88 (KERNEL32.DLL.wine_get_unix_file_name+0x21eb30):  b7a21fb8 100e3603 b26320e0 00000002
0xb7a21f98 (KERNEL32.DLL.wine_get_unix_file_name+0x21eb40):  00000000 b2632610 b7a22154 b2632630
0xb7a21fa8 (KERNEL32.DLL.wine_get_unix_file_name+0x21eb50):  b26322c4 b2632630 b26320e0 00000012
0xb7a21fb8 (KERNEL32.DLL.wine_get_unix_file_name+0x21eb60):  b7a21ff8 100e7dd8 00000000 00000002
0xb7a21fc8 (KERNEL32.DLL.wine_get_unix_file_name+0x21eb70):  b2632610 00000000 b2632630 b2632740
0xb7a21fd8 (KERNEL32.DLL.wine_get_unix_file_name+0x21eb80):

Backtrace:
=>0 0x100e2c52 (EQGRAPHICSDX9.DLL.CreateGraphicsEngine+0xd6312 in C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\EQGRAPHICSDX9.DLL) (ebp=b7a21f88)
  1 0x100e3603 (EQGRAPHICSDX9.DLL.CreateGraphicsEngine+0xd6cc3 in C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\EQGRAPHICSDX9.DLL) (ebp=b7a21fb8)
  2 0x100e7dd8 (EQGRAPHICSDX9.DLL.CreateGraphicsEngine+0xdb498 in C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\EQGRAPHICSDX9.DLL) (ebp=b7a21ff8)
  3 0x10091699 (EQGRAPHICSDX9.DLL.CreateGraphicsEngine+0x84d59 in C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\EQGRAPHICSDX9.DLL) (ebp=b7a22148)
  4 0x100070e5 (EQGRAPHICSDX9.DLL..text+0x60e5 in C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\EQGRAPHICSDX9.DLL) (ebp=b2632730)

0x100e2c52 (EQGRAPHICSDX9.DLL.CreateGraphicsEngine+0xd6312 in C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\EQGRAPHICSDX9.DLL): cmpl  $3,0x0(%eax)
Modules:
Address                 Module  Name
0xb4315000-b4363200     (PE)    C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\DPVS.DLL0xb4374000-b4376000     (PE)    D3D9.DLL
0xb5da9000-b5dab000     (PE)    D3DGL.DLL
0xb6429000-b642b000     (PE)    MIDIMAP.DRV
0xb6430000-b6432000     (PE)    MSACM.DRV
0xb658a000-b658c000     (PE)    MSACM32.DLL
0xb659a000-b659c000     (PE)    WINEOSS.DRV
0xb674f000-b6751000     (PE)    X11DRV.DLL
0xb6874000-b6876000     (PE)    COMCTL32.DLL
0xb6909000-b690b000     (PE)    SHLWAPI.DLL
0xb6990000-b6992000     (PE)    SHELL32.DLL
0xb6a08000-b6a0a000     (PE)    RPCRT4.DLL
0xb6a4a000-b6a4c000     (PE)    OLE32.DLL
0xb6a93000-b6a95000     (PE)    LZ32.DLL
0xb6a9a000-b6a9c000     (PE)    VERSION.DLL
0xb6aa1000-b6ab4200     (PE)    C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\DSETUP.DLL
0xb6abb000-b6abd000     (PE)    IMM32.DLL
0xb74e8000-b74ea000     (PE)    DDRAW.DLL
0xb7523000-b7525000     (PE)    DINPUT.DLL
0xb753c000-b753e000     (PE)    DINPUT8.DLL
0xb7546000-b7548000     (PE)    IPHLPAPI.DLL
0xb7556000-b7558000     (PE)    WS2_32.DLL
0xb756a000-b756c000     (PE)    WSOCK32.DLL
0xb7581000-b7583000     (PE)    WINMM.DLL
0xb75db000-b75dd000     (PE)    ADVAPI32.DLL
0xb760f000-b7611000     (PE)    GDI32.DLL
0xb769e000-b76a0000     (PE)    USER32.DLL
0xb77c2000-b77c4000     (PE)    KERNEL32.DLL
0xb7f25000-b7f27000     (PE)    NTDLL.DLL
0x00400000-00990000     (PE)    C:\Program Files\Sony\EverQuest Trilogy\eqgame.exe
0x10000000-10c7c000     (PE)    C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\EQGRAPHICSDX9.DLL
0x21100000-2115e600     (PE)    C:\PROGRAM FILES\SONY\EVERQUEST TRILOGY\MSS32.DLL
Threads:
process  tid      prio
00000001 (D) C:\Program Files\Sony\EverQuest Trilogy\eqgame.exe
        00000003    0
        00000002    0 <==
WineDbg terminated on pid 1
wine client perror:3: sendmsg: Bad file descriptor
``` 

sorry for the length of that.

-Phreek

---

### Post by sandmanfvr on 2005-09-07
Check on Transgaming.org for bugs and fixes.  I had to for World of Warcraft.  It will take some time fiddling with it, but now I run WOW full speed and it is great.  NO Windows.

---

