---
title: "urgent help - data recovery"
date: 2006-01-30
forum: Desktop Environments
---

### Post by Bou on 2006-01-30
Hi, I had a blackout this afternoon, and when the light came back two hours later my main hard drive didn't seem to work.

It's still not working, I installed Ubuntu on a spare HD but my computer won't even start up if the main HD is plugged. Is there any utility that can help me check if there's any recoverable data on it?

I have personal pictures and stuff there, as well as important documents I was currently working with, so it would be extremely important to recover them. Thank you in advance, whether you can help me or not.

---

### Post by dcstar on 2006-01-30
[QUOTE=Bou]Hi, I had a blackout this afternoon, and when the light came back two hours later my main hard drive didn't seem to work.

It's still not working, I installed Ubuntu on a spare HD but my computer won't even start up if the main HD is plugged. Is there any utility that can help me check if there's any recoverable data on it?
........[/QUOTE]
No "utility" will work on dead hardware.

You may be able to find a local computer repair shop to work on your hard drive, the other option is to send it to a specialised data recovery organisation to work on it (expensive).

Depending on the actual fault, it may be an option to obtain another working drive of the same model, and swap the electronics over to get access to the platters on the faulty drive - but you also need an expert to do this.

You may end up spending many, many hours (and dollars) trying to recover the data, you may also get lucky, welcome to the world of computing.

---

### Post by mustang on 2006-01-30
Did you try making your spare HD (that you're using right now) the primary master? So then the supposedly broken one is primary slave? That way you could eliminate the possibility that the hard drive is just having a problem booting but the contents are still there

---

### Post by Bou on 2006-01-30
[QUOTE=mustang]Did you try making your spare HD (that you're using right now) the primary master? So then the supposedly broken one is primary slave? That way you could eliminate the possibility that the hard drive is just having a problem booting but the contents are still there[/QUOTE]

That's what I did, Mustang. The only yhing I got was an "error 5" while booting. Not that I know what that is, anyway.

---

### Post by mustang on 2006-01-30
Hmm weird. I'm sure more people with more experienced observations will chime in but you could try borrowing or buying a hard drive enclosure and connecting that through firewire/usb and see if that works.

I'm just throwing some suggestions around as I know how it feels to lose precious data. Hope you work out your problem my friend.

---

### Post by Bou on 2006-01-30
Thanks a lot for your help and, most important, for your support :) I really appreciate it.

---

### Post by amohanty on 2006-01-30
>  "error 5" 

Did you encounter this while booting off of the spare HDD via Ubuntu? One possible reason is that grub if installed in mbr will know of your broken drives partitions and as such will break if you dont plug in an similar hdd with similar partition tbl.

Heres what you can do:
1. Plug in the spare hdd as primary master, the broken one as primary slave.
2. Install Ubuntu install CD and restore grub via instructions at:
[http://ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub)
this essentially re-setsup grub
3. Now that grub is setup for your spare hdd, try booting off of it.
4. Next do a :
> sudo GParted
If you dont have it install using :
> sudo apt-get install GParted
This will show you all hdds and partitions that are ok. 

If you cannot see your partitions on the second hdd, well you are screwed and will need professional tools or help to recover data. If you do see the partitions on the broken hdd, then simply mount the partitions and copy off the files.

HTH
AM

---

### Post by xmastree on 2006-01-30
There is one option I've read about (but never tried). if the controller board is damaged but the actual **data** is still ok, if you can get hold of an **identical** drive, you can swap over the PCBs.

---

