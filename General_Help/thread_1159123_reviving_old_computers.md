---
title: "reviving old computers"
date: 2009-05-14
forum: General Help
---

### Post by fabiete on 2009-05-14
Cheers everyone!
Im am new to this forum but I have been using Ubuntu (8.04, EeeBuntu 8.10 on a netbook and lately 9.04) for a while and I find it excellent.
I often read of people resuscitating old computers by installing Linux, so I tried to do this on a friend's machine (Pentum III, 512Mb RAM, Intel CC820 motherboard).  Ubuntu (both 8.04 and 9.04) won't install due to problems with the graphics adaptor.  After searching on the web I found out that in such situations the alternate version, with text-based installation procedure, should be used instead.  When I tried this there was a warning on the BIOS version (pre-year-2000) but I tried anyway to continue since I could not look for an update on internet.  The installation went on up to 76% and then stopped.  I have now looked for an upgrade and there is indeed a later version of the BIOS (P09).  The question is: is it worthwhile going through the hassle or should I tell my colleague to dump his pc?  Has anyone got any experience on computer CPR? Thanks in advance.

---

### Post by whoop on 2009-05-14
Well IMO it would be a shame to throw it away. So I would try to update the BIOS firmware (and I wouldn't even call it a hassle ;) )
You might want to go a little lighter than ubuntu (although it should run). Maybe try Xubuntu?

---

### Post by CatKiller on 2009-05-14
If you're going to tell your friend to get a new computer anyway, then there's no harm in risking bricking the old one with a bad BIOS flash. It might work and save them the expense of buying a new computer. That computer should be OK for Ubuntu, and run Xubuntu pretty well.

There are kernel options that you can use to get around the finicky nature of old motherboards, but you can probably search them out and tell if they're applicable to that motherboard just as fast as I could.

As long as the process doesn't get interrupted and the update is for that **specific** motherboard, it should go OK. Might help, might not. Worth a try, though, I reckon.

---

### Post by petrus4 on 2009-05-14
> **fabiete said:**
> 
I often read of people resuscitating old computers by installing Linux

Do not try to do this with Ubuntu; its' hardware support is currently flakey enough on contemporary hardware, let alone old stuff.

Get either Damn Small Linux, Aardvark Linux I think it's called, or Puppy Linux.  All three of those distributions are designed either for embedded stuff, or older/less powerful hardware.  Also go to DistroWatch.com and have a look for whatever other distros are there that are specialised for that use.

If researching something before you do it is also new to you, welcome to Linux. ;)

---

### Post by CatKiller on 2009-05-14
> **petrus4 said:**
> Do not try to do this with Ubuntu; its' hardware support is currently flakey enough on contemporary hardware, let alone old stuff.

Hardware support generally has to be reverse-engineered. The fact that bleeding-edge stuff might not work yet is pretty much orthogonal to whether old stuff will work. A P3 with 512MB of RAM doesn't really need the extremely stripped-down focus of something like DSL; it's not like we're looking at a 486 here. DSL is an incredible achievement, but I wouldn't recommend it to a new user.

---

### Post by cap'n leaky on 2009-05-14
I agree with CatKiller, you should be fine running Ubuntu or if needed Xubuntu.

My day to day home machine is very similar:
Built in 2002, Intel mobo - socket 370 with celeron 1.4 GHz, 512Mb ram, and I've upgraded from the onboard video to an AGP nVidia GeForce 5200 (yes, it's an antique).

I originally loaded Xubuntu Hardy and have been disto upgrading at each release.  I am running 9.04 now, and everything runs faster than XP on this machine (I dual boot).  As long as I turn off desktop effects, everything runs smooth. I went back to Gnome as the DE, and even that runs acceptably to me.

It should be enough horsepower, and it will be an easier distro that using Puppy or DSL.  You could always try one of those if things are too slow, or you could load a lighter WM from Ubuntu.  I also have LXDE, WM and Fluxbox loaded and they all run really well.  LXDE is Windows like enough that it may be a good option.

---

### Post by Iusedtowearatie on 2009-05-14
I would start with Xubuntu. If that fails, DSL or Puppy are fine, but perhaps a bit... simplistic. I have successfully revived a few really old machines with TinyMe ([http://tinymelinux.com/doku.php](http://tinymelinux.com/doku.php)) which has a reasonably elegant interface, uses Synaptic package handling and still requires very limited HW resources.

---

### Post by ushills on 2009-05-14
Install a command line only ubuntu then add either lxde or xcfe with apt-get.  this will give you a bare bones window manager that you can add what you want to.

---

### Post by ugm6hr on 2009-05-14
Revived plenty of old computers, often before donating them to other people.

The specs you gave should cope with Ubuntu, although the key is to get something working.  Xubuntu or Ubuntu+XFCE is a reasonable place to start.  I have installed Xubuntu 8.04 on something similar (P3 + 256MB RAM), and found it perfectly usable.

I think a BIOS update is definitely worthwhile; some boards can be updated with USB or CD-R (rather than floppies).

---

### Post by dsimpson on 2009-05-15
If it wasn't possible then I wouldn't be here. I have a Dell computer and did a BIOS upgrade, I don't really know if it was necessary or if it improved anything. It is a P3, dual 933Mhz processors, 512Mb ram, 9Gb SCSI Primary HD, 30Gb Secondary HD for file storage. Running Ubuntu 9.04 with no problems, just don't have the fancy Nvidia Graphics and can't run Compiz but I am computing fine as a home unit, it all depends on what the computer is going to be used for. My computer is a 1999 year model, so if your graphics card is an issue, it may just need another. Some people choose to run older equipment, others can only afford to run old equipment, I am in the later category, so only you know how important this computer is to your friend. Good luck with your decision.:D

---

### Post by fabiete on 2009-05-24
Hello there!

First of all thanks for everyone's advice.

News update now: I finally managed to upgrade the BIOS of the old machine (not really straightforward since I discovered, after multiple attempts and one floppy drive change, that the bleeding thing would not work via floppy) then went on to install Ubuntu.  The system now does not stop where it used to but still fails to install.  I tried the live version first and it goes on until the desktop shows. The mouse works for a few seconds then everything freezes. I tried to install directly but in that case the problem arises before the screen with the language choice appears.  I have not tried the alternate version yet.

DSL works but it won't do for the owner of the PC.

I shall have a go at Xubuntu and/or have a look at distrowatch to see what other options are available.

Cheers.

---

### Post by Steve_Barker on 2009-05-24
With the specs you have I would go for TinyMe, or Sam 2007 (I've found the newer version is not quite as flexible on older machines), I've used these on several older machines and they have worked well. 

If you can add ram that is useful.

---

