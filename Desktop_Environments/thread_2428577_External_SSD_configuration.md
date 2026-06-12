---
title: "External SSD configuration"
date: 2019-10-05
forum: Desktop Environments
---

### Post by ubuntini2 on 2019-10-05
On Ubuntu (Mate) 18.04.1 LTS 
Just reformatted an external 1TB SSD to NTFS using the built in Disks utility.

First question 
Is there a way to make external drives mount on the desktop like you can with OSX?

2nd question
Why doesn't my new drive appear under /media/<user>/ ?

3rd question
Is there a way to change the mnt name  (at /mnt/) to something more descriptive?

Lastly, if yes to #3, can this name be consisted with what is viewable at /media/<user>/  ?

---

### Post by yancek on 2019-10-05
I doubt if external drive partition mount points are the Desktlop but then I've never used a Mac so can't really say.  Most likely that is just a link.  On the other hand, I suppose you could create a mount point on  user Desktop though that might create problems, depending upon what the drive is used for.l 
Does anything show under /media/username?  UUID's?
What do you want to change under /mnt?  You can create a mount point there for an external drive partition and create a proper entry in the /etc/fstab file to have it mount there on boot.  You can give the mount point any name you wish.
Not sure what you are asking in question 3 as you earlier indicate you don't see the windows partition under /media/username.

---

