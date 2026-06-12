---
title: "dosemu"
date: 2005-10-31
forum: Gaming &amp; Leisure
---

### Post by TragicWarrior on 2005-10-31
After using Fedora Core 1-4 for such a long time, I've decided to try the Ubuntu ship.  I am very used to "yum install dosemu" and everything just works (minus editing autoexec.bat and config.sys).

Using Breezy Badger, I did apt-get for dosemu, dosemu-freedos, and xfonts-dosemu.  When I run xdosemu, it immediately bombs with info below.  Any thoughts?

ERROR: cpu exception in dosemu code outside of VM86()!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x468a5b2d
eip: 0x468a5b2d  esp: 0xbfc9ffc5  eflags: 0x00010286
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x468a5b2d
CPU was in user mode
Exception was caused by non-available page
/usr/bin/xdosemu: line 218: 16542 Segmentation fault      $SUDO $BINARY $XFLAG "$@"

---

### Post by Harleen on 2005-10-31
Dosemu is a real pain to set up correctly. I haven't even tried it under Ubuntu yet, because dosbox does all I need and is much easier to configure. If you can get over losing some performance in DOS application, you should try dosbox and forget about dosemu.

---

### Post by Tulip on 2005-11-16
I'm getting the same error on startup. Im trying to run a DOS POS (Point of Sale :)) program on Ubuntu. I got it running on DosBox initially, but then discovered there is no printer support to LPT1 in DosBox - no receipts. Im struggling through the Dosemu documentation but finding it pretty hard going. Can anyone point me in the right direction please?

---

### Post by ChrisDerson on 2005-11-17
I've been having the same problem with DOSEmu on Breezy.  I noted that the breezy version is 1.2.1.0 (dosemu.bin --version), I also noted that under Fedora Core 2 DOSEmu 1.2.2.0 works fine (guess where this is going ;) ).

Did a little checking and found a 1.2.2.0 Debian package for DOSEmu in the [malyjarda]("http://ftp.malyjarda.cz/pub/Linux/DOSEmu/Debian/sarge/i386/") Debian Sarge repository.

Removed the existing DOSEmu and FreeDOS packages from my system, downloaded [dosemu_1.2.2-1_i386.deb]("http://ftp.malyjarda.cz/pub/Linux/DOSEmu/Debian/sarge/i386/dosemu/dosemu_1.2.2-1_i386.deb"), [xfonts-dosemu_1.2.2-1_all.deb]("http://ftp.malyjarda.cz/pub/Linux/DOSEmu/Debian/sarge/i386/dosemu/xfonts-dosemu_1.2.2-1_all.deb") and also [dosemu-freedos_b9r5-1_i386.deb]("http://ftp.malyjarda.cz/pub/Linux/DOSEmu/Debian/sarge/i386/freedos/dosemu-freedos_b9r5-1_i386.deb")
then used dpkg -i to install them.  Voila, xdosemu now pops up a C:> prompt :D.

Hope this helps.

---

### Post by slux on 2005-11-17
Sounds like the package is flawed, that kind of an error indicates a fundamental problem with the binary. 

Dosemu isn't that hard to set up if everything is well with the package itself. I think people should always try it for their needs before going to dosbox since dosbox is just so slow compared to it for now. Windows people don't have a choice but Linuxists do.

---

### Post by Ruskie on 2005-12-15
[QUOTE=TragicWarrior]After using Fedora Core 1-4 for such a long time, I've decided to try the Ubuntu ship.  I am very used to "yum install dosemu" and everything just works (minus editing autoexec.bat and config.sys).

Using Breezy Badger, I did apt-get for dosemu, dosemu-freedos, and xfonts-dosemu.  When I run xdosemu, it immediately bombs with info below.  Any thoughts?

ERROR: cpu exception in dosemu code outside of VM86()!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x468a5b2d
eip: 0x468a5b2d  esp: 0xbfc9ffc5  eflags: 0x00010286
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x468a5b2d
CPU was in user mode
Exception was caused by non-available page
/usr/bin/xdosemu: line 218: 16542 Segmentation fault      $SUDO $BINARY $XFLAG "$@"[/QUOTE]

Just one: I run in the exactly same problem, both in X and in console (Ctrl-Alt-F[1..5]. If I found something I'll let you know. :)

---

### Post by ChrisC on 2005-12-18
I had the exact same problem with the v1.2.1 found in the repository.  Hearing above that 1.2.2 might work better, I tried for an hour to get the "malyjarda" repository to work in Synaptic, failed miserably.  Downloaded the debs instead and installed them with dpkg.  Still doesn't work, although this time it's a different error: "cpu exception in dosemu code outside of VM86".  Sigh.

---

### Post by Ruskie on 2005-12-18
using chrisderson hints I could run dosemu with minimal effort.

---

### Post by ChrisC on 2005-12-18
Yeah, that's what I tried too, ain't working.  I'm now investigating DOSbox, which is a shame because I had all this working on the hoary system that I had set up as a trial run prior to the committed dive into Ubuntu that I'm weathering now.

---

### Post by Ruskie on 2005-12-20
It didn't work for me. It runs perfect in Windows (Using frontend called D-fend to launch it), but on Linux I can't type the colon carachter, and you know that is fundamental in DOS...
It didn't type it in Windows as well, but if I type Shift-&#242; (that's where it is in US keyboard I believe) it works... If I do so in Linux it doesn't. Coludn't bother to smuggle with keymaps... :)

---

### Post by bouh on 2005-12-25
I do not run ubuntu (but Debian). But your problem as NOTHING to do with:
1 - Package configuration (distrib)
2 - User Configuration

It's a know issue with dosemu since kernel 2.6.12 because of virtual address randomization.

To correct this, as superuser, type:
echo 0 > /proc/sys/kernel/randomize_va_space

Now you can run dosemu. Enjoy.

---

### Post by flurl on 2006-01-30
thx to bouh, 
his tip worked great for me :-)

---

### Post by Kuprin on 2006-01-31
I've never had any problems running games in DosBox - anything you actually need DosBox for will run at full speed on any modern system; my box can easily clock DosBox up to about a gigahertz with no slowdown, allowing 512MB of usable RAM, and I'm not that tweaked at this point (it was tricked out when I bought it, but that was almost two years ago now).

---

### Post by rogeriovinhal on 2006-03-24
Does anyone know how to make a keymap for DOSEMU?

I have a Brazillian ABNT2 keyboard, and would be nice to make it work on DOSEMU.

---

### Post by yellow beard on 2006-05-03
I tried using dosemu and it was a pain in the ***. Dosbox worked straight away though, i suggest giving it a go if you havent already.

---

### Post by bensode on 2006-05-13
[QUOTE=bouh]
To correct this, as superuser, type:
echo 0 > /proc/sys/kernel/randomize_va_space

Now you can run dosemu. Enjoy.[/QUOTE]

running that even with sudo yields:

bash: /proc/sys/kernel/randomize_va_space: Permission denied

](*,) 

You must become root first before trying to write this or it will fail.  To become root, use:

sudo su -
(enter sudo password)

then run "echo 0 > /proc/sys/kernel/randomize_va_space" at the # (root) prompt, then exit.  Now xdosemu and dosemu work

---

### Post by DaveNF2G on 2006-07-08
I've tried the root user command to randomize VA space and it had no effect.  

I also tried to obtain the 1.222 Debian files, but the repository in question is password protected.

I will need the fastest DOS emulator I can get for the realtime serial digital decoding applications that I run, so I don't think Dosbox will suffice.

BTW, I never got any error messages at all with DOSEMU.  **Absolutely nothing happened** when I clicked on its launcher.

Any new ideas (some of this thread is several months old now) for DOS under Dapper?

The current repository version of DOSEMU is 1.2.2-3build1 .

---

### Post by jISh on 2006-07-09
Well, there's the VMWare and FreeDOS option that not many seem to have considered.

However, I can see why, because it's a real pain to set up. I've been working with it, I did manage to get it installed, however there are a few errors and also I don't know how to access my Linux filesystem from inside the VMWare machine.

If you want to give it a go, check out [Peturrr's Tutorial]("http://www.ubuntuforums.org/showthread.php?t=183209") on VMWare/Windows XP, just use the tutorial up to the part where you go to install Windows XP, and instead install FreeDOS from [http://www.freedos.org](http://www.freedos.org)

---

### Post by DaveNF2G on 2006-07-13
I figured out how to use dosemu.  It has to be run from the terminal, like dosbox.  I don't know why the install package puts a launcher on the desktop.  It can't be started that way.

---

### Post by Kimmo_S on 2006-08-08
Josip Rodin wrote, on Wed, Oct 19 2005 on linux.debian.bugs.dist in
Bug#327153: dosemu: fails to start

> I also get a very similar error:

> % xdosemu
> ERROR: cpu exception in dosemu code outside of VM86()!
> trapno: 0x0e  errorcode: 0x00000005  cr2: 0xffffff8e
> eip: 0x000069ee  esp: 0xbfb5ffcc  eflags: 0x00010246
> cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
> Page fault: read instruction to linear address: 0xffffff8e
> CPU was in user mode
> Exception was caused by insufficient privilege
> ERROR: leavedos() called from within a signal context!

> I worked around the problem by downloading
> [http://freedos.sourceforge.net/freecom/packages/082pl3/xmsswap.zip](http://freedos.sourceforge.net/freecom/packages/082pl3/xmsswap.zip)
> and using command.com from it as /usr/lib/dosemu/commands/comcom.com .

---

### Post by AustinMarton on 2007-11-04
I'm in fiesty and did apt-get install dosemu and it all works perfectly.

One problem though - it's damn slow! No dos game is playable at this speed. 

Is there a way to speed it up? a command to start the virtual machine  with more ram?

Cheers.
Austin.

---

### Post by emendelson on 2007-11-05
Check out the "hogthreshold" setting in dosemu.conf and search the web for information about setting it.

---

### Post by AustinMarton on 2007-11-06
I tried dosbox and it ran at a much nicer speed without any setup.

---

