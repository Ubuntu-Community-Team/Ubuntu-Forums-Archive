---
title: "CD-ROM Device File Path"
date: 2009-03-18
forum: General Help
---

### Post by rebornempowered on 2009-03-18
This is an extremely noob type question and I appreciate any help that can be offered.

I am attempting to install a CD/DVD Duplicator software called Turbojet 2.  I have everything set but cannot figure out the device file of my CD-ROM.

Here is a screen shot of what I am seeing.

[IMG]http://stpaulsandusky.org/youthfiles/planningfiles/Screenshot-1.png[/IMG]

Where can I find the paths for my three CD-ROM drives?

---

### Post by circa82 on 2009-03-18
Check the /media directory as that's generally where removable media (CD/DVD's & USB drives) are automatically mounted. You will need a CD in each drive you're working with, otherwise it won't show.

---

### Post by kryptikos on 2009-03-18
Hard to say what it is looking for. Does the turbojet manual / README / docs say anything about what it is looking for there? circa82 is right, if there is a cd loaded it will mount to /media/cdrom generally speaking. However if it is actually wanting to reference the hardware so it knows to tie to it, it may be looking for /dev/cdrom which is a softlink to the actual device. 

I may be a little biased, but K3b is the best Linux burner out there IMHO. It will do everything you want it to do including duplication.

---

