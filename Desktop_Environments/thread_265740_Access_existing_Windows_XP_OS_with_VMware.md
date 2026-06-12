---
title: "Access existing Windows XP OS with VMware?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by pimpaulogy on 2006-09-26
How do you access an already existing Windows XP OS on a separate partition?  Basically, I have XP on my laptop, and then I created a partition with the free space and install Ubuntu.  Now, I would like to use VMware (player or server, doesn't matter which) to access my existing XP partition without reinstalling XP.  All howto's I found talked about installing XP, not using an pre-existing OS.

Thank you for your help.

---

### Post by sharkcohen on 2006-09-26
You won't be able to use vmware to do what you are asking, that is fundamentally not how vmware works.

---

### Post by pimpaulogy on 2006-09-26
If that is the case, can there be anything else done to do what I am looking to do.  It's just a pain to reboot if I want to access my already configured XP.

---

### Post by dentaku65 on 2006-09-26
> **sharkcohen said:**
> You won't be able to use vmware to do what you are asking, that is fundamentally not how vmware works.

Why?
I'm working very well with vmware server on Ubuntu loading XP home installed on the other partition of my disk.
See this howto [http://yep.it/?5izxdd](http://yep.it/?5izxdd) not specific for Ubuntu but quite simple to adapt.

---

### Post by pimpaulogy on 2006-09-26
Thank you, thank you, thank you for that link to the how to.  I am going to try it, but looking through the steps, it all makes sense.  Crossing fingers and toes.

---

### Post by dentaku65 on 2006-09-26
> **pimpaulogy said:**
> Thank you, thank you, thank you for that link to the how to.  I am going to try it, but looking through the steps, it all makes sense.  Crossing fingers and toes.

I discard all the part regarding the creation of the virtual floppy, when I load the virtualization in vmware I've be VERY CAREFUL in grub to choose quickly the XP Windows entry (I have 10 seconds of delay). Please BE AWARE to do not choose the partition of the OS where vmware is loaded!!

---

### Post by sharkcohen on 2006-09-26
Wow, sorry, I didn't know vmware could be used like that!

---

### Post by dentaku65 on 2006-09-26
> **sharkcohen said:**
> Wow, sorry, I didn't know vmware could be used like that!

The only stupid thing is that M$ ask again when you load your already installed xp on your hard disk in virtualization mode the product key code :evil:

---

### Post by Henry Rayker on 2006-09-26
does it ask only the first time, or does it ask each time?

---

### Post by dentaku65 on 2006-09-26
> **Henry Rayker said:**
> does it ask only the first time, or does it ask each time?

Asks like if you did a new installation, but in fact you did not, just virtualize the already installed one... weird and waste of time.

---

### Post by pimpaulogy on 2006-09-26
Well, I guess I didn't get all my fingers crossed in time because it's not working.  I am stuck at the point:
Followed all install intructions, except for creating new bootloader.  That's an after the fact anyways.
Launched the VM image.
Got the Grub menu
Selected XP
See the command that it normally launches (with chainloader and whatnot)
And it just sits there.  Nothing else happens.

I can still launch my XP normally (outside of VMware) but it just sits there when launching with VMware.

Any ideas?

---

### Post by dentaku65 on 2006-09-26
Try to load it from the shell to see the errors if any.
See also this howto from Gentoo [http://yep.it/?pinmwj](http://yep.it/?pinmwj)

---

### Post by pimpaulogy on 2006-09-26
I got VMware Server to launch again.  Don't know why setting changed, but permissions were removed so I had to set them up again.  That issue is resolved.

Unfortunately, still can't launch my existing XP from within VMware Server.

---

