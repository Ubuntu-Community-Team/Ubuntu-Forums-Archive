---
title: "Ubuntu -&gt; Reading PSX CD-ROM"
date: 2008-06-12
forum: Gaming &amp; Leisure
---

### Post by ludek_cortex on 2008-06-12
Hello
I have a little problem.
I have a dvd recorder (/dev/scd0/) and normal cd-rom (/dev/scd1). When I put PlayStation CD into the recorder it reads it without any errors. But If I put the CD into cd-rom disk isn't even spinning...
I didn't have this problem on Windows. Can someone help me?

(btw. sorry for my english)

---

### Post by acoustibop on 2008-06-12
Are you talking about running a game from the CD in an emulator, ludek_cortex, or simply browsing the contents of the CD?  And what emulator (if that's what you're commenting on) and what game(s) are you talking about?  And what versions of Linux and Windows are you talking about?

If you're talking about browsing the CDs; this is not unusual; I always find that drives won't read my Playstation CDs if I put them in - this is not because they can't, but (I'm not sure why, but it's probably because the CDs are not seen as data, music or video CDs) but because they're not automatically mounted.  You simply need to mount the CD.

It may be that you've set your DVD-RW to mount anything it can read, while leaving your CD-ROM on the standard setting.

If you're talking about an emulator reading the disc, this may be a copy protection issue: many drives have problems reading protected discs and, generally, -RW drives are better than -ROM drives at this.

Without more information, though, it's difficult to say.

---

### Post by ludek_cortex on 2008-06-12
Well I was talking about both situations (browsing and running from emulator). I belive that emu don't want to read cD because it isn't mounted (as you mentioned).... But when I'm trying to mount it with sudo mount -t iso9660 /dev/scd1 /media/cdrom0 I only getting this error:
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so 

dmesg | tail returned this:
[26851.129753] end_request: I/O error, dev sr1, sector 64
[26851.130138] isofs_fill_super: bread failed, dev=sr1, iso_blknum=16, block=16

---

### Post by acoustibop on 2008-06-12
You still haven't said what emulator(s) and OS versions you're talking about, ludek_cortex.

However, with most emulators (certainly pSX), you *shouldn't* mount the CD: the emulator reads the drive as a device from its entry in /dev, not from the mount point.

For browsing a CD, don't mount to /media/cdrom0, but first create a folder to mount to in /mnt, then mount to that folder, eg:```
sudo mount -t iso9660 /dev/scd1 /mnt/<folder>
``` where <folder> is the folder you've created.

---

### Post by ludek_cortex on 2008-06-13
OS - Hardy
Emu - epsxe 1.6
Tried mounting in /mnt/cdrom folder but it's still giving me error from the previous post...

fstab entry for dvd recorder and cdrom:
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

---

### Post by acoustibop on 2008-06-13
You chose the painful way, ludek_cortex.  Most people are switching to [pSX Emulator]("http://psxemulator.gazaxian.com/"): it works so much better than ePSXe; it's more accurate and much simpler.

---

### Post by ludek_cortex on 2008-06-13
I don't want to know which emu should I use.... All I want to know is how to use PSX CDs in my cd-rom drive :P

Btw. even if I put the cd into the cdrom and try run it in pSX or epsxe the disc isn't even spinning....

---

### Post by Grishka on 2008-06-13
> **ludek_cortex said:**
> I don't want to know which emu should I use.... All I want to know is how to use PSX CDs in my cd-rom drive :P

Btw. even if I put the cd into the cdrom and try run it in pSX or epsxe the disc isn't even spinning....

man, just change your cd-drive already. it's broken, ok? ;)

---

### Post by ludek_cortex on 2008-06-13
It's not broken :P Everything works on Windows (installed that only to test this) but not on Linux :P

---

### Post by acoustibop on 2008-06-13
You need to make your mind up about what you want, ludek_cortex.  Do you want to browse Playstation CDs?  Mount them.  See my second post in this thread.

Do you want to play them from CD?  Use pSX Emulator.  See my third post for the link.  Or use ePSXe.  But realise there's a *lot* of very awkward setting up and configuring to do with it - and when pSX works so much better anyway, it's a no brainer.

If you want to use pSX on a Ubuntu OS, you'll need to install libgtkglext1 (in the repositories), download the pSX package and unpack it where you want it, put a BIOS in the bios subfolder and run it.  As long as you've got a working soundcard and 3d videocard, that's it: it's a pluginless emulator, so configuration is minimal (most people can run it quite happily with the default configuration except for controller configuration).

Or carry on struggling with ePSXe - your choice.  Just don't blame me if it gives you no end of problems and doesn't work as well as pSX even when (and if) you get it working.  I did tell you.

**Edit:** you still haven't told us yet what games you're trying to play, and what Windows OS you're using.  If your CD won't run in pSX, the likelihood is the game's protected, it has a compatibility problem, the CD is damaged, or there's a problem with your drive.  Every Playstation game I have I can run from CD in pSX with my DVD-RW drive, but I can't run copy protected games in my DVD-ROM drive because it doesn't read subcode.  Unprotected games work fine.

---

### Post by ludek_cortex on 2008-06-13
I just wanted to know why my cd-rom don't want to read psx cds  (well I can't both play or browse psx cd if it's in the cdrom... sorry for my laconic posts). I tried games like Final Fantasy VII, FF Tactics, Crash Bandicoot, Wild 9...

---

### Post by acoustibop on 2008-06-13
Final Fantasy VII is the only one of those games I have and play; my PAL version plays fine and neither the PAL nor NTSC versions are protected.  However, all the Final Fantasy games originally made for the Playstation (i.e. Final Fantasies VII, VIII and IX) seem to be very sensitive to surface damage: many people have reported that even with only light scuffing (much less than would stop other games playing) the game won't play.  While I bought my copy of Final Fantasy VII new and have kept it in good condition, my first copies of Final Fantasies VIII and IX were second hand but seemed in good condition.  Neither would play properly however, but when I bought new copies - no problem!

I have a copy of Wild 9 but never played the game much - mine plays fine, though.

The NTSC-US version of Final Fantasy Tactics (there are no reports for the PAL version - I don't know if there is one) is in the Compatibility Lists for pSX as playing, but with a possible crash.  Crash Bandicoot is reported as playing fine in both NTSC-US and PAL versions.

So your games should be playing.  Did you try the method I suggested for mounting your games?  If that doesn't work, that strongly suggests there's a problem with the drive.

**Edit:** are these original Playstation CDs or burned copies?

---

### Post by ludek_cortex on 2008-06-14
Originals. But I tried copies also ;) And yes, I'm tried mouting but it gives error:

"mount: wrong fs type, bad option, bad superblock on /dev/scd1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so"

---

### Post by acoustibop on 2008-06-14
Did you try the method I suggested, ludek_cortex?  And does mounting work on your DVD-RW?

---

### Post by ludek_cortex on 2008-06-14
Yes, I tried it, mounting works on dvd-rw but not on cd-rom

---

### Post by acoustibop on 2008-06-14
Does sound like there's something wrong with your cd-rom or the way it's configured in your system, ludek_cortex.

However, there's one thing you could try, especially if you haven't rebooted since trying any mounting attempts - do```
sudo umount <path to any mounting attempts you've made>
```
From your early posts, this could include```
sudo umount /media/cdrom0
```and, if you tried the message I mentioned,```
sudo umount /mnt/<folder>
```where <folder> is the folder you created for mounting CDs to.

Otherwise, just reboot.

---

### Post by ludek_cortex on 2008-06-14
It helped! :) Thank you mr acoustibop.

---

### Post by acoustibop on 2008-06-14
Ah!  It must have been that at some point you successfully mounted a CD and, not having unmounted it, the drive wouldn't read anything else.

---

### Post by qwerty800 on 2009-04-20
Hi there!

I searched as much as humanly possible, I didn't found anything.
I posted in so many forums in so many languages and I'm now out of ideas.

I just want to **mount a PSX CD**, so that I could **browse** in it and extract the soundtrack.

There is nothing wrong with my CD/DVD-Drive since PCSX is perfectly able to run the game.

I tried with **Wine** ([http://download.consolemul.com/Utils/Playstation/PsxMC301.zip]("http://download.consolemul.com/Utils/Playstation/PsxMC301.zip")), with **Cdemu**, I looked on every single page of data that Google and Ixquick handeled to me, I tried with **Acetone ISO** and pray for somebody to help me!

Each time I tried to use my wine soft, it resulted in a major crash (Kernel Panic).

And I don't know what to do with mount, since it asks me to specify the filesystem type. And I can't say that it's an ISO 9660 because it is not.

:(

---

### Post by zero777zero on 2009-04-20
PSX emulation is best when you are emulating from hard drive not CD drive

here is a guide to dump your games
[http://redump.org/guide/](http://redump.org/guide/)

---

### Post by qwerty800 on 2009-04-21
Hum...

Every software I used until now (includind IsoBuster) Referred me to two files, totalising about 500 kB while my BIN archive weight 600 MB.

I would say that my file is corrupted, but...
How could PCSX read it, then?

Screw this, I'll download what I want directly from Redump.org!

Thanks for the link!:KS

---

### Post by qwerty800 on 2009-04-22
> **qwerty800 said:**
> Every software I used until now (includind IsoBuster) Referred me to two files, totalising about 500 kB while my BIN archive weight 600 MB.


Ok, I searched once again, and discovered that Chrono Cross is a special case.

[The datas are kind of hidden trough the CD.]("http://www.tales-cless.org/docs/thepsxdoc.txt")

It's really weird and I'll try to find some more about that.

---

### Post by qwerty800 on 2009-04-25
I finally simply used my windows software on the someone else's Windows box.

It's probably the only way to do this.:sad:

---

### Post by bikodog on 2009-05-24
Thanks for the help on this thread acoustibop; i was having the same problem with psx discs.

I just finished using your tips and AcetoneISO to make an image of Dragon Warrior VII. It's running great in pSX v1.13.

---

