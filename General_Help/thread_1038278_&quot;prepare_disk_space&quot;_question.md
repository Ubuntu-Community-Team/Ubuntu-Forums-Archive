---
title: "&quot;prepare disk space&quot; question"
date: 2009-01-12
forum: General Help
---

### Post by firsttimeuser on 2009-01-12
Just got my new laptop with vista pre-installed, and I am trying to load ubuntu 8.10 onto it, the question is:

at the "prepare disk space" stage, if I choose "Guided -resize", it appears ubuntu will only take max 61% of the 120G disk and I can not force it to grab anymore disk space.

I figured "Manual" is the way to go, but I am not sure how can I do it. I googled for a while and does not see a straightforward example how can I preserve the existing vista OS and shrink the windows partition.

anyone can share me a good example?

---

### Post by Snow986 on 2009-01-12
Well.. You need to edit the windows partition to whatever size you want according to how much you want to give ubuntu.  Just select it and select edit partition( i think thats the button).  Then after resizing the windows partition, create a new one and give it say 512MB or 1 GB and use as swap.  Then create your Ubuntu partition with whatever is left over.  Use format "ext3" and mount point "/" will be fine. Then let it do the rest.

---

### Post by firsttimeuser on 2009-01-12
hmm, i am not quite sure how can I do it.

I boot the system using unetboot tool and I don't see windows partition in ubuntu thus nothing I can select to modify the partition size.

> **Snow986 said:**
> Well.. You need to edit the windows partition to whatever size you want according to how much you want to give ubuntu.  Just select it and select edit partition( i think thats the button).  Then after resizing the windows partition, create a new one and give it say 512MB or 1 GB and use as swap.  Then create your Ubuntu partition with whatever is left over.  Use format "ext3" and mount point "/" will be fine. Then let it do the rest.

---

### Post by cariboo on 2009-01-12
I'm not to familiar with the Vista disk management tool, but apparently for best results you need to resize your Vista partition with the disk management tools in Vista. Once you have made the desired space, you can then use the LiveCD to install Ubuntu.

Jim

---

### Post by firsttimeuser on 2009-01-12
thanks, i just tired to use vista's disk management tool, but the max free disk I can get from it is about 30G, and it refuse to go any further.

Looks like vista has some kind of disk proection running which won't allow me to free a big chunk of disk space. 

Still doing research now...

---

### Post by Universal344 on 2009-01-12
OK go to the start menu and type computer management.  Right click and say run as administrator (unless you are admin, than just proceed).  Once in expand storage on the left panel and click disk management.  Then right click your main vista partition and click shrink.  Choose an amount to shrink and wait for it to shrink.  Than run the installer for Ubuntu and under manual click on the free space and click new partition.  Under type select Linux Swap.  Make that about equal to your RAM and you can make it logical.  Then make a new partition again and make it EXT3 journaling, primary, enter the amount of disk space you have left (or less if you want extra)  and make the mount point "/".  Hope that helps.

EDIT: if you can't shrink vistas partition any further 30gb is probably enough for Ubuntu unless you plan on doing a lot with it and installing a lot of applications.

---

### Post by cariboo on 2009-01-12
I forgot to mention one thing, you should defrag Vista at least twice, this may allow you some more free disk space.

Jim

---

### Post by firsttimeuser on 2009-01-12
:) thanks for the long input, i tried and vista won't allow me to shrink more than 30G, which is really stupid.

I know 30G is enough, actully when I install from CD, ubuntu says it can give me 60G, but... I just don't want to waste 60G on windows.

> **Universal344 said:**
> OK go to the start menu and type computer management.  Right click and say run as administrator (unless you are admin, than just proceed).  Once in expand storage on the left panel and click disk management.  Then right click your main vista partition and click shrink.  Choose an amount to shrink and wait for it to shrink.  Than run the installer for Ubuntu and under manual click on the free space and click new partition.  Under type select Linux Swap.  Make that about equal to your RAM and you can make it logical.  Then make a new partition again and make it EXT3 journaling, primary, enter the amount of disk space you have left (or less if you want extra)  and make the mount point "/".  Hope that helps.

EDIT: if you can't shrink vistas partition any further 30gb is probably enough for Ubuntu unless you plan on doing a lot with it and installing a lot of applications.

---

### Post by Universal344 on 2009-01-12
Hmm...

So ubuntu is telling you that there is 60gb free space when you could only free 30gb?  If so than are you sure there isn't some free space on your drive by default?  Do you know if it came bundled with backup software that put the backup on a hidden partition (like Acronis Trueimage or Norton Ghost)?

Also, you should try defragging like cariboo907 said and try running disk cleanup.

---

