---
title: "Problem Installing Ubuntu..."
date: 2006-04-05
forum: Desktop Environments
---

### Post by jan4x4 on 2006-04-05
Hello!
Here's the problem... I loaded the CD in the CD-ROM of my laptop.. Then when it reached and fininshed installing the base system... the screen turns into blank:confused:  and after a while a messege went out of the screen. The messege was: "Segmentation Fault".](*,) 

My system's a HP Compaq Presario 2100.

Anybody Help!!!! Plz..

---

### Post by frodon on 2006-04-05
Strange, because the wiki doesn't report this problem : [https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresario2100](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresario2100)
Maybe you should try to download and burn another install CD.

---

### Post by Darkriser on 2006-04-05
I'll join this thread as I expected very similar kind of error:

I recently wanted to try Dapper Flight 6 CD. But I was unable to finish the installation. Everytime, the "Installing base system" phase failed. What's more weird, it keeps failing at different stages (percent completed). It simply freezes. But after switching to console #4 (debug), there's always the same message: Segmentation fault!

Just to add - I'm running Breezy by default and had no problems installing it (several times). My PC is desktop with Intel P4 2.4MHz and 1.5GB RAM.

Anyone has an idea?
Thanx

---

### Post by mar29 on 2006-07-21
I have a AJP Neo PC II from about 5 years ago. I downloaded the livecd but it would randomly crash in gnome and restart the session losing the install process, so I downloaded the alternative install cd and it would randomly halt during the install and going to alt+f4 showed that it was a segmentation fault on each occasion, i tried to test the cd and got the same fault. I took the cd out and tried it on my up-to-date pc and the cd is fine! The Neo PC has a laptop motherboard and uses SIS chipset that has shared video memory. It has Windows Me on the pc which works fine and it seems like the disk, memory and cd drives are working fine!

---

### Post by ssodhi on 2006-07-23
My knowledge of memory management is rusty, to say the least, but iirc segmentation is kind of link paging.

What did you do as far as a swap partition goes?

---

### Post by mar29 on 2007-01-11
I'd forgotten completely about this.
The problem of the seg fault harrassed me and I tried different distros:
Debian 3, Fedora Core, OpenSuse and then out of the blue Mandriva worked so have kept to that. I'm not going to sort the problem out but cannot understand it. I doubt it is to do with swap space as the PC in question would produce the seg faults when loading from Debian's 2 floppy disk net install, and with 256mb ram I'm sure it should have been able to handle the boot up on 2 floppy disks... oh well. if anyone else has this problem and can't work it out try Mandriva (2006 version worked for me)

---

### Post by vlad.b on 2007-01-11
I had a similar problem and still do. My only option is using Fedora 6, which unfortunately dosent even see my wireless nor my 56K modem. Guess I will have to put my lazyness aside for a bit and work on getting them to work cause Fedora is gonna be my desktop's operating system for some time. Under Ubuntu Edgy, they both worked out of the box. It's time's like these that I think that there are too many distributions out there and too many great developers scattered all over the place.

---

