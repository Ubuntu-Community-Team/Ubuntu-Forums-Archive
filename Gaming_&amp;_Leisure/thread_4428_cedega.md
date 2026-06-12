---
title: "cedega"
date: 2004-11-15
forum: Gaming &amp; Leisure
---

### Post by im_ka on 2004-11-15
hi!

i'm gonna convert my lil brothers... but that won't happen without cedega.

i've downloaded a file called "cedega.tar.gz" (no, not from their website :))
could anyone come up with a step-by-step howto? i've never used an emulator (not even wine).

thanks in advance

---

### Post by az on 2004-11-15
First step:  Untar the archive:
Open up a terminal
tar xvzf cedega*
cd cedega*

read the README.

That is as far as anyone can go without knowing anything else.


If you need to compile stuff, (yes, probably so.) install build-essential.

Use synaptic, the package manager.

---

### Post by HiddenWolf on 2004-11-15
[QUOTE=azz]First step:  Untar the archive:
Open up a terminal
tar xvzf cedega*
cd cedega*

read the README.

That is as far as anyone can go without knowing anything else.


If you need to compile stuff, (yes, probably so.) install build-essential.

Use synaptic, the package manager.[/QUOTE]

/me begs cedega would grow more stable, and support more games.

---

### Post by im_ka on 2004-11-15
[QUOTE=azz]First step:  Untar the archive:
Open up a terminal
tar xvzf cedega*
cd cedega*

read the README.

That is as far as anyone can go without knowing anything else.


If you need to compile stuff, (yes, probably so.) install build-essential.

Use synaptic, the package manager.[/QUOTE]

if i untar it, it's all in a "usr" dir. no make file, nothing to compile.

[http://www.unet.univie.ac.at/~a0201073/files/cedega.tar.gz](http://www.unet.univie.ac.at/~a0201073/files/cedega.tar.gz)

---

### Post by az on 2004-11-15
Sounds like trouble to me.  Tris is a pre-build version with no documentation.  You don`t know for what system it is made or what binaries you need.

Useless.

---

### Post by zenwhen on 2004-11-15
Transgaming offers to its subscribers a .deb installer for Cedega that works perfecty.

---

### Post by jdodson on 2004-11-15
[http://uic.nnov.ru/~gaav10/cedega4.1/](http://uic.nnov.ru/~gaav10/cedega4.1/)

dont run it all in one place :-P 

btw, google searches can really help out :-P

---

### Post by zenwhen on 2004-11-15
Or you could do that.   :wink: ^^

---

### Post by TravisNewman on 2004-11-15
Not so sure how legal that is... but we'll assume that it was built from CVS :)

---

### Post by HungSquirrel on 2004-11-15
If this actually works for me, you just became my new best friend.  It runs installers okay, which is more than I could do on my previous attempts at wine/winex/cedega.

> Not so sure how legal that is...
> [http://uic.nnov](http://uic.nnov)**_.ru_**/~gaav10/cedega4.1/
Well, in my experience with that domain extension... ;)

---

### Post by jdodson on 2004-11-15
as legal as decss or mplayer :-P

and somewhere i have found .rpms of cedega built from CVS source, which is legal.  this souce had a .deb that is why i linked it.  anyways, it seems odd to me that wineX got its codebase from wine, and then decided to not make it free(as in freedom).  they also said they would give code back to wine, which to my knowledge they have not done much of.   this is just easier than CVS, but in the end you get the same thing.

---

### Post by HungSquirrel on 2004-11-15
Well, it works...sort of.  It runs Deus Ex (an ancient game!) at ~20fps on my $300 Radeon 9800 video card.

Does anyone have any tips/tricks for making cedega run better?

---

### Post by jdodson on 2004-11-15
[http://transgaming.org/forum/](http://transgaming.org/forum/)

---

### Post by im_ka on 2004-11-15
[QUOTE=jdodson][http://uic.nnov.ru/~gaav10/cedega4.1/](http://uic.nnov.ru/~gaav10/cedega4.1/)

dont run it all in one place :-P 

btw, google searches can really help out :-P[/QUOTE]

thanks!

point2play is just an advanced (gui-ish) cedega, isn't it?

---

### Post by jdodson on 2004-11-15
[QUOTE=im_ka]thanks!

point2play is just an advanced (gui-ish) cedega, isn't it?[/QUOTE]

from what i understand it is a GUI way to install windows games in a more "easy" manner.

---

### Post by TravisNewman on 2004-11-15
[QUOTE=jdodson]from what i understand it is a GUI way to install windows games in a more "easy" manner.[/QUOTE]
 That's exactly it. It's not really THAT much easier though, honestly. It does some of the work for you, but you know more of what's going on, and can therefore diagnose problems easier, if you don't use it. Again, that's my experience, but I like to tweak and do things with the command line ;)

---

### Post by HiddenWolf on 2004-11-16
Is there any chance in hell of one of these platforms growing up once and allowing me to play very recent windows games at decent rates?

---

### Post by TravisNewman on 2004-11-16
Hmm... Doom 3 plays better through Cedega than it does on Windows... maybe something to do with your ATI drivers and xorg, since the two people complaining of slow rates have ATIs in xorg.

---

### Post by zenwhen on 2004-11-16
My choice to buy a Nvidia 6800 was made almost totally because I was tired of dealing with issues like that. Although their drivers are closed, choosing them leaves your options wide open.  8)

---

### Post by HungSquirrel on 2004-11-16
[QUOTE=panickedthumb]Hmm... Doom 3 plays better through Cedega than it does on Windows... maybe something to do with your ATI drivers and xorg, since the two people complaining of slow rates have ATIs in xorg.[/QUOTE]
 Actually, I have an ATi in XFree 4.3.  (I haven't jumped on the Hoary bandwagon yet.)

---

### Post by TravisNewman on 2004-11-16
Ah.

Well maybe its an ATi thing? I installed DeusEx just to see if I could replicate what you were saying, and it runs very smoothly at the highest detail levels.

---

### Post by fng on 2004-11-16
it just works
great!

---

### Post by HiddenWolf on 2004-11-17
[QUOTE=panickedthumb]Hmm... Doom 3 plays better through Cedega than it does on Windows... maybe something to do with your ATI drivers and xorg, since the two people complaining of slow rates have ATIs in xorg.[/QUOTE]
It's not Xorg, it's not ATI.

I'm not running the ATI drivers.
I will not be playing a decent game under linux untill I buy myself a decent pc. Meaning a pci-x a64/nvidia based system.

The only game I *really* Would want to see on Linux is Rome: Total War. And it annoys me that that probably won't happen anytime soon.

There are three reasons for me to boot into windows, in order of importance:
- The windows software I sell
- The R:TW game
- Photoshop (yeah, I hate gimp)

---

### Post by HiddenWolf on 2004-11-17
[QUOTE=panickedthumb]Ah.

Well maybe its an ATi thing? I installed DeusEx just to see if I could replicate what you were saying, and it runs very smoothly at the highest detail levels.[/QUOTE]

ATI, ugh. I'll never buy an ATI card again. :-)

---

### Post by maus on 2004-11-17
I'm having issues with lockups, but it might be a hardware problem. Is there a way I can throttle cedega down to using only, say, 75% of my free CPU cycles?

---

### Post by duff on 2004-11-17
[QUOTE=maus]I'm having issues with lockups, but it might be a hardware problem. Is there a way I can throttle cedega down to using only, say, 75% of my free CPU cycles?[/QUOTE]
check the `nice` command

---

### Post by jdodson on 2004-11-17
[QUOTE=maus]I'm having issues with lockups, but it might be a hardware problem. Is there a way I can throttle cedega down to using only, say, 75% of my free CPU cycles?[/QUOTE]

you might have some luck using [http://www.computerhope.com/unix/unice.htm](http://www.computerhope.com/unix/unice.htm) the "nice" command, however your lockups, etc might be from a faulty config/driver or old hardware or cedega just plain cant do it, its attempting to pretend its windows, that comes at a reliablity and speed cost.

---

### Post by jdong on 2004-11-17
[http://www.cs.wisc.edu/~ghost/doc/cvs/Public.htm](http://www.cs.wisc.edu/~ghost/doc/cvs/Public.htm)

1. Licenses.

Licensor hereby grants you the following rights, provided that you comply with all of the restrictions set forth in this License and provided, further, that you distribute an unmodified copy of this License with the Program:

(a)
    You may copy and distribute literal (i.e., verbatim) copies of the Program's source code as you receive it throughout the world, in any medium. 
(b)
    You may modify the Program, create works based on the Program and distribute copies of such throughout the world, in any medium. 




seems legal to me!

---

### Post by fng on 2004-11-18
Since the USN-29-1 update, cedega stopped working.
Are you guys experiencing the same plroblem?

---

### Post by fng on 2004-11-18
nevermind ... :/

I didnt even had 3d rendering
Rebooting the desktop fixed all the problems

---

### Post by HungSquirrel on 2004-11-18
I swapped my awesome ATI card for my roommate's mediocre Nvidia card, and Deus Ex now works in cedega.  At least, works better.  I still don't get 60 fps in game unless I'm staring at a wall.

Meh.  I'll live.  If I can get Steam/CSS/HL2 to work in cedega, I will be quite content with the setup.  Unfortunately I can't get Steam to finish updating during the install using the package with HL precached.  Has anyone else tried to install and update Steam?

---

### Post by fng on 2004-11-19
I got steam working here with cedega and my ati.

Before you start asking me all sorts of hl-related questions : I'm no cs player, more  a hater :). Quakers unite! Play more promode!

I just tried steam out, hoping i could play cssource with my czero key (no i didnt buy it :), i would never do that! it was in the box of an ati-card i instaled for a friend). I read it somewhere on a newssite, that it was possible. But it doesnt work. I cant update cssource in steam. 

HL + all mods work fine.

fng

---

### Post by HungSquirrel on 2004-11-19
```
esheldon@sage ~ $ cedega /fat/shared/apps/steaminstall_halflife.exe
ReadStyleSheet: missing style number
Last token read was "}" near line 2, position 22.
esheldon@sage ~ $ wineserver: not enough memory for allocation of 124923907 bytes
start=0x90001000 present=0x9001d054 total=0x405f48
```
That occurs right after it finishes the update and gets ready to launch Steam.  Same error occurs if I try to launch Steam after the update.  :(

---

### Post by im_ka on 2004-11-20
how do you install games that come on more cd's? i'm using pure cedega (point2play doesn't seem to be fully working) from that russian site.

i wanna install mafia, and after it's done with the 1st cd and asks for cd2, i can't unmount it. i've tried unmount -l (lazy), but then it can't read cd2...

suggestions, experiences?

---

### Post by zenwhen on 2004-11-20
If you add the " --monitor-cdrom-eject" switch when you run the installer, you will be able to eject the cd when a game asks for a new one.

---

### Post by dacman on 2004-11-27
Hey evry1, I have some problems with my cedega, when I try to install WC3 this is what I get-- ```
Warning: Language 'en_HR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
wine: Unhandled exception, starting debugger...
Warning: Language 'en_HR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega/winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000c690
No debug information in ELF '/usr/lib/transgaming_cedega/winex/pthread_lib/libntdll.so' (0x40018000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/pthread_lib/libwine.so' (0x40119000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libwine_unicode.so' (0x4012e000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libwine_port.so' (0x401f5000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x40201000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x40224000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x4035f000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x40370000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libole32.so' (0x40703000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libadvapi32.so' (0x40768000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libkernel32.so' (0x4078f000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libuser32.so' (0x4080f000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libgdi32.so' (0x40938000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/librpcrt4.so' (0x409ad000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libwinmm.so' (0x409f3000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libversion.so' (0x40a49000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/liblz32.so' (0x40a53000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libshell32.so' (0x40a5a000)
No debug information in ELF '/usr/lib/transgaming_point2play/lib/libpng.so.3' (0x40ad5000)
No debug information in ELF '/usr/lib/libz.so.1' (0x40b0c000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libshlwapi.so' (0x40b1e000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libcomctl32.so' (0x40b5e000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libwineserver.so' (0x40be3000)
No debug information in ELF '/usr/lib/libfreetype.so.6' (0x40c2e000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libx11drv.so' (0x40c9b000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libwine_tsx11.so' (0x40d17000)
No debug information in ELF '/usr/X11R6/lib/libSM.so.6' (0x40d33000)
No debug information in ELF '/usr/X11R6/lib/libICE.so.6' (0x40d3c000)
No debug information in ELF '/usr/lib/libGL.so.1' (0x40d53000)
No debug information in ELF '/usr/lib/transgaming_cedega/winex/lib/libGLU.so.1' (0x40dc1000)
No debug information in ELF '/usr/X11R6/lib/libXext.so.6' (0x40e7c000)
No debug information in ELF '/usr/X11R6/lib/libX11.so.6' (0x40e8a000)
No debug information in ELF '/usr/lib/libGLcore.so.1' (0x40f51000)
No debug information in ELF '/usr/lib/tls/libnvidia-tls.so.1' (0x41642000)
No debug information in 32bit DLL 'H:\install.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40055000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0x407c2000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0x4077a000)
No debug information in 32bit DLL 'GDI32.DLL' (0x40957000)
No debug information in 32bit DLL 'USER32.DLL' (0x40846000)
No debug information in 32bit DLL 'RPCRT4.DLL' (0x409d0000)
No debug information in 32bit DLL 'OLE32.DLL' (0x40722000)
No debug information in 32bit DLL 'C:\WINDOWS\SYSTEM32\MSVCRT.DLL' (0x78000000)
No debug information in 32bit DLL 'WINMM.DLL' (0x40a01000)
No debug information in 32bit DLL 'LZ32.DLL' (0x40a56000)
No debug information in 32bit DLL 'VERSION.DLL' (0x40a4c000)
No debug information in 32bit DLL 'SHLWAPI.DLL' (0x40b3b000)
No debug information in 32bit DLL 'COMCTL32.DLL' (0x40b6c000)
No debug information in 32bit DLL 'SHELL32.DLL' (0x40a80000)
Unhandled exception: page fault on write access to 0x40da3154 in 32-bit code (0x4164231a).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:4164231a ESP:406f1ed4 EBP:406f1f1c EFLAGS:00010246(  R- 00  I  Z- -P1 )
 EAX:40da3154 EBX:00000000 ECX:ffffffb8 EDX:00000006
 ESI:080786d0 EDI:08077ad8
Stack dump:
0x406f1ed4 (NTDLL.DLL.memcpy+0x451af4):  40d7ad45 40d883e2 40016c00 080786d0
0x406f1ee4 (NTDLL.DLL.memcpy+0x451b04):  08077ad8 406f1f1c 406f1f1c 4000c0de
0x406f1ef4 (NTDLL.DLL.memcpy+0x451b14):  00000006 bffff444 bffff460 403614cc
0x406f1f04 (NTDLL.DLL.memcpy+0x451b24):  4022cbec 40298a94 00000000 40016c00
0x406f1f14 (NTDLL.DLL.memcpy+0x451b34):  0000000a 08077ad8 406f1f5c 4000c1ca
0x406f1f24 (NTDLL.DLL.memcpy+0x451b44):  080786d0 00000006 bffff444 bffff460
0x406f1f34 (NTDLL.DLL.memcpy+0x451b54):

Backtrace:
=>0 0x4164231a (COMCTL32.DLL.SmoothScrollWindow+0xa9d48e in libnvidia-tls.so.1) (ebp=406f1f1c)
  1 0x4000c1ca (NTDLL.DLL.wine_dbg_printf+0x37fc3a2e in ld-linux.so.2) (ebp=406f1f5c)
  2 0x40331f52 (NTDLL.DLL.memcpy+0x91b72 in libc.so.6) (ebp=406f1fcc)
  3 0x4000bf26 (NTDLL.DLL.wine_dbg_printf+0x37fc378a in ld-linux.so.2) (ebp=406f20cc)
  4 0x40331b3a (NTDLL.DLL.memcpy+0x9175a in libc.so.6) (ebp=406f215c)
  5 0x40370fdb (NTDLL.DLL.memcpy+0xd0bfb in libdl.so.2) (ebp=406f226c)
  6 0x40371446 (NTDLL.DLL.memcpy+0xd1066 in libdl.so.2) (ebp=406f2294)
  7 0x00000002 (ebp=080696e9)
  8 0x72643131 (COMCTL32.DLL.SmoothScrollWindow+0x31a9e2a5) (ebp=7862696c)
*** Invalid address 0x7862696c (MSVCRT.DLL..reloc+0x5e396c)

0x4164231a (COMCTL32.DLL.SmoothScrollWindow+0xa9d48e in libnvidia-tls.so.1): movl       %ecx,0x0(%eax)
Modules:
Address                 Module  Name
0x00400000-00457000     (PE)    H:\install.exe
0x40055000-40057000     (PE)    NTDLL.DLL
0x40722000-40724000     (PE)    OLE32.DLL
0x4077a000-4077c000     (PE)    ADVAPI32.DLL
0x407c2000-407c4000     (PE)    KERNEL32.DLL
0x40846000-40848000     (PE)    USER32.DLL
0x40957000-40959000     (PE)    GDI32.DLL
0x409d0000-409d2000     (PE)    RPCRT4.DLL
0x40a01000-40a03000     (PE)    WINMM.DLL
0x40a4c000-40a4e000     (PE)    VERSION.DLL
0x40a56000-40a58000     (PE)    LZ32.DLL
0x40a80000-40a82000     (PE)    SHELL32.DLL
0x40b3b000-40b3d000     (PE)    SHLWAPI.DLL
0x40b6c000-40b6e000     (PE)    COMCTL32.DLL
0x78000000-78046000     (PE)    C:\WINDOWS\SYSTEM32\MSVCRT.DLL
Threads:
process  tid      prio
00000001 (D) H:\install.exe
        00000002    0 <==
WineDbg terminated on pid 1
wine client perror:2: sendmsg: Bad file descriptor
wine client perror:2: sendmsg: Bad file descriptor

```

I would appriciate any help, 10x

---

### Post by Marauder1 on 2004-11-28
2 quetions for you Cedega experts ...

1 - Which video card is better for it ? ( ATI or Nvidia )

2 - I have an Nvidia Geforce 3 ti-200 and i'd like to know
     if i would be able to play some games with it or do i
     have to replace it ?

TIA

---

### Post by HungSquirrel on 2004-11-28
I have had better luck with my mediocre Nvidia card than I have with my nearly top of the line ATI.  But that is just my personal experience.

GF3 Ti200s are great cards.  I used to own one.  It played UT2003 pretty well in Linux, so I imagine you can play a lot of good games with it without needing to upgrade.

---

### Post by kal_zakath on 2004-11-28
Answers : 

1 - Nvidia

2 - Should be enough for games that are not too new (Don't think you will enjoy playing HL² with this card on cedega)

---

### Post by Marauder1 on 2004-11-29
thanks guys i might stick another year with it ...
But since cedega is an emulator does it effect
the speed of the games a lot ? ( what pourcentage less).
Can you run some games in a window to get
more speed. (like doom2 in linux use to do ) ?

---

### Post by nehalem on 2004-11-29
[QUOTE=HungSquirrel]I swapped my awesome ATI card for my roommate's mediocre Nvidia card, and Deus Ex now works in cedega.  At least, works better.  I still don't get 60 fps in game unless I'm staring at a wall.

Meh.  I'll live.  If I can get Steam/CSS/HL2 to work in cedega, I will be quite content with the setup.  Unfortunately I can't get Steam to finish updating during the install using the package with HL precached.  Has anyone else tried to install and update Steam?[/QUOTE]

Actually this is surprising to me.  I have the 9800 Pro with the ATI drivers installed and Doom3 even performs surprisingly well (No shader stuff so the eye candy is defenitley down a few big notches).

Deus Ex is like forever old.  How wierd.

---

### Post by HungSquirrel on 2004-11-29
[QUOTE=zenwhen]If you add the " --monitor-cdrom-eject" switch when you run the installer, you will be able to eject the cd when a game asks for a new one.[/QUOTE]
 When I do that, I still cannot eject the CDROM, nor can I unmount the drive (even as root).

---

### Post by flix on 2004-11-30
thanks, my cs is running =P~ 
little bit laggy more then normal but can live with that :-)

---

### Post by LinuxDev on 2004-12-03
Thank you all, I've jsut installed cedega and steam to play Half Life Team Fortress Classic, and it works smooth ;) I get 72 fps :)
I have a Geforce 6800.

My only excuse to sometime boot back to XP was the games, but now, I can play on Ubuntu, great ;) thanks again :)

---

### Post by mattyh on 2004-12-04
I like Cedega a lot, but every distro I run it on has issues w/ not being able to recognize the cd, due to the protection.  It REALLY annoys me.  I think I'll fire up Diablo 2 once just to see if it works, but I'm pretty sure it didn't work for me before.  Either did Warcraft 3.  I can't remember if I tried it on an earlier install of Ubuntu or not.

---

### Post by subterrific on 2004-12-05
[QUOTE=HungSquirrel]When I do that, I still cannot eject the CDROM, nor can I unmount the drive (even as root).[/QUOTE]

Yeah, --monitor-cdrom-eject doesn't work on Ubuntu because it uses pmount to mount removable media, such as cdroms, automatically. I don't understand the internals, but apparently it isn't compatible with mount/umount

I read in the wine docs that the other way to eject a cd is to send wineserver SIGUSR2, so: "killall -USR2 wineserver" will eject the cd.

---

### Post by brdweb on 2004-12-07
[QUOTE=subterrific]Yeah, --monitor-cdrom-eject doesn't work on Ubuntu because it uses pmount to mount removable media, such as cdroms, automatically. I don't understand the internals, but apparently it isn't compatible with mount/umount

I read in the wine docs that the other way to eject a cd is to send wineserver SIGUSR2, so: "killall -USR2 wineserver" will eject the cd.[/QUOTE]
 Actually I don't think that last statement is actually true. When you use point2play to power cedega, it does the mounting / unmounting just fine and I think that's still actually cedega code. I had to do this when I installed World of Warcraft, which if you follow the tips on the unofficial Transgaming wiki, runs just fine I'm happy to report.

---

