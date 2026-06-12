---
title: "Clean my hard drive."
date: 2005-12-08
forum: General Help
---

### Post by jbrader on 2005-12-08
I need a good way to make sure that everything that's on my hard disk now is tottally gone. But I don't want to bork the disk in the process because I plan on doing a clean install after. Does anybody know how to do this using the live cd?
Thanks in advance.

---

### Post by codejunkie on 2005-12-08
[quote=jbrader]I need a good way to make sure that everything that's on my hard disk now is tottally gone. But I don't want to bork the disk in the process because I plan on doing a clean install after. Does anybody know how to do this using the live cd?
Thanks in advance.[/quote]
exactly what do you mean by gone, do you just want to delete the partition and make a new one do you want to zero the drive, or wipe all traces of data that were on the drive and then partition and format the drive?

---

### Post by jbrader on 2005-12-08
Wipe all traces of data. I already know hot to partition and all that, I´ve done that lots of times.

---

### Post by Rinzwind on 2005-12-08
Just start the new install.
During setup you will be asked to do with your disc and choose: use complete disc.

That'll erase it all afaik.

---

### Post by raydel on 2005-12-08
What you want to do is perform a Low Level Format.  This will write zeros to all the tracks on the drive.  Years ago, there were utilies in motherboard BIOSes that would do this.  But, I haven't seen one in a BIOS since Pentiums came out ten years ago.  I'll bet you someone has made a utility for linux.  Search for "low level format" @ google.com/linux.

---

### Post by soulestream on 2005-12-08
formatting the drive on a new install will be enough.

Low level formatting can mess the drive up and anybody who wants to get data off the drive that bad can get it off after a low level format too. 

I used to go to extremes to erase data, till i saw someone recover 75% of a drive after it had been erased and smashed with a hammer.

If you need a true secure erase of data you need to zero the drive about 10 times, smash it and burn it. Its what the government does. ;) 


soule

---

### Post by mherring on 2005-12-08
If you really need a secure wipe, get a utility for the purpose  (Search on Google for "disk wipe utilities"---there are a bazillion)

The one I use is a Linux installation on a floppy.  You boot from it, type a few commands and that's it.  I cant get the name without actually booting it and I will not risk this here.

Otherwise, just format and install

---

### Post by codejunkie on 2005-12-08
[quote=mherring]If you really need a secure wipe, get a utility for the purpose  (Search on Google for "disk wipe utilities"---there are a bazillion)

The one I use is a Linux installation on a floppy.  You boot from it, type a few commands and that's it.  I cant get the name without actually booting it and I will not risk this here.

Otherwise, just format and install[/quote]
are you talking about the shred command mherring? and [jbrader]("http://ubuntuforums.org/member.php?u=3428") i dont remember the way to do it with the live cd but there is an easy program called autoclave that uses the shred command you just download it to a floppy or cd and boot to it, and choose the drive to use, and the amount of passes and random data to write to the drive but just writing zero's to the drive will not erase all the data on it.

---

### Post by mherring on 2005-12-08
No--I was referring to a real wipe utility which includes the mil-spec routines for destroying classified data.  

I FOUND it!!!!  Darik's boot and nuke:

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

I've used this several times---works like a charm (AND it's Linux!)

---

### Post by dishkuvek on 2005-12-08
Check the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") out.  It's got a handful of utilities on a bootable cd.  I used it when I needed to recover lost data.  There should be something on there for you.

---

### Post by jbrader on 2005-12-09
Thanks a bunch everybody. I guess I have to get to work on that now.

---

