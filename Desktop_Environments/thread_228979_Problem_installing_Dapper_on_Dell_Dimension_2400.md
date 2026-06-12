---
title: "Problem installing Dapper on Dell Dimension 2400"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Budreaux on 2006-08-03
Hopefully someone can help me with this install.  I am trying to get Dapper installed on a Dell Dim. 2400 and when i get to "Starting Kernel Log", I get the following error:

Buffer I/O error on device hdc

I have tried one other hard drive (Segate 545Mb) with the same result.  I'm kinda new to linux and can't read enough into the error to help myself.

Below are the specs of the pc:

Intel Celeron 2.4 Ghz
256 Meg Ram
80 Gig Segate HD

Thanks,

Budreaux

---

### Post by orb9220 on 2006-08-03
Well hdc is normally your cdrom mine is hdc.

Which dapper are you using desktop? 386? or 686?

It also could be a problem with the cd dics did you download and burn the iso?

---

### Post by Budreaux on 2006-08-03
orb,

I downloaded the desktop ISO and burned to a CD.  If you need any further info, let me know.

thanks,

Budreaux

---

### Post by orb9220 on 2006-08-03
Could find only this thread. And indications if image was burned to an rw instead of a standard -r +r disk.

rw are notorious for being unreliable.

[http://www.ubuntuforums.org/showthread.php?t=220703](http://www.ubuntuforums.org/showthread.php?t=220703)

---

### Post by Budreaux on 2006-08-04
orb,

I had also found that thread, however I wasn't sure what I was supposed to do.  When I hit F6 at the initial menu, I get one line of text towards the bottom.  I typed in the "irqpoll", but it didn't work.  From what you said about hdc, and reading the error more, I think the disc I used may be to blame.  I am going to download again from a different mirror and burn another CD.  I'll let you know what happens.

---

### Post by Budreaux on 2006-08-08
Ok, I used a different brand of cd and dapper loaded.  I do have a new question now though.  Is the install supposed to be painfully slow?  I am at the second screen of the install (set time and date) and have been here for the past 30 minutes.  The mouse movement is intermittant and I cannot select anything.  The CD drive light flashes intermittantly as well as the hard drive light.  Is this how the install is supposed to go?

---

### Post by bulldog on 2006-08-08
It should go quicker,but I'm not sure how your 256 MB memory is to blame.
I have 1 Gyg and the install was about 20 minutes.

Maybe you should check the disc first before you attempt to install.

You could try to use the alternate version and not the live cd.
This should be less hard on your memory.

---

### Post by Budreaux on 2006-08-08
bulldog,

what's the alternate version and where do I get it?  Thanks.

---

### Post by tabweb on 2006-08-08
The Alternate cd, allows text based install, doesn't have the live CD on it, etc... go here : [http://ubuntu-releases.cs.umn.edu//6.06/]("http://ubuntu-releases.cs.umn.edu//6.06/") and scroll down and you'll see the Alternate cd options. 

I don't think this will be much help. I also don't think the 256mb memory is an issue. I would make sure to check your md5 after you download and burn. I think it sounds more like an installation media issue. Good luck

---

### Post by Budreaux on 2006-08-08
tabweb,

Thanks for the help.  The alternate version did the trick.  I think the 256meg ram was somewhat to blame.  I now have Ubuntu installed and will fully test the system tomorrow.  Thanks everyone for their help.

---

