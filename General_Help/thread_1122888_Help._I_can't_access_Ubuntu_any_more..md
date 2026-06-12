---
title: "Help. I can't access Ubuntu any more."
date: 2009-04-11
forum: General Help
---

### Post by John Jones on 2009-04-11
I've been using Ubuntu for about 3 years now, but I occasionally like to look at other distros. I thought I'd have a look at the newest OpenSuse distro, so I downloaded and installed it. Didn't much like it, (couldn't access Ubuntu any more, for one thing), so I did what I usually do if a distro leaves me unable to load other OS's, I deleted OpenSuse and installed Ubuntu on that partition. Normally, this then gives me access to all the other OS's on my PC.

On this occasion, all I got was error 22 (whatever that is!). I tried a couple more times and got the same result. I then dug out my XP CD (I have Windows on a small HDD; SDA1, and several Linux distros on a larger drive; SDB1, etc.), and ran FIXMBR. After that, I was able to load XP (I'm writing this in XP), so I re-installed Ubuntu, expecting that I would get the usual Grub menu on booting up.

Instead of that, my PC now boots straight into XP. Can anybody help me with this please? 

Also, I assume there's a better way of sorting out Grub problems than by installing Ubuntu again. I've tried reading the literature on Grub, and I don't understand it. Is there a beginner's guide to Grub? I know enough to edit menu.lst to some extent, but I don't know how to make the PC boot from another version of Ubuntu that already exists on my HDD (I don't even know enough to explain my problem properly!)

Help, please!

John Jones

---

### Post by John Jones on 2009-04-11
Some additional info; I've just been comparing menu.lst files, and it seems that the hard drive that was called hd0 (which has XP on it), is now called hd1, and the drive that was called hd1 (where all my Linux distros are) is now called hd0.

Is this relevant to the problem I described earlier? And is there anything I can do about it?

Cheers,

John

---

### Post by schmidtbag on 2009-04-11
I'm not sure what that error means but what always helped me fix my MBR problems was Super GRUB.  It can be burned to a CD or put on a floppy disk.  I've never used it for Linux boot issues.  Its free too, search it on google, it should be one of the first results.

Just so you know, this doesn't fix your boot loader, it just lets you boot into an OS that doesn't have one.  so, when ubuntu starts up, what you should do is purge grub and then reinstall it, and i'd think that'd fix the problem.

---

### Post by John Jones on 2009-04-11
Thanks, Schmidtbag, I'll give it a go.

Cheers,

John

---

### Post by John Jones on 2009-04-12
> **schmidtbag said:**
> I'm not sure what that error means but what always helped me fix my MBR problems was Super GRUB.  It can be burned to a CD or put on a floppy disk.  I've never used it for Linux boot issues.  Its free too, search it on google, it should be one of the first results.

Just so you know, this doesn't fix your boot loader, it just lets you boot into an OS that doesn't have one.  so, when ubuntu starts up, what you should do is purge grub and then reinstall it, and i'd think that'd fix the problem.

I don't know what it did, but Super GRUB seems to have cured my problem.

Thanks a million,

John

---

