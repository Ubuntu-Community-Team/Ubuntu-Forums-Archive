---
title: "Disk usage!!"
date: 2009-05-26
forum: General Help
---

### Post by meet.aman7 on 2009-05-26
Does the image and the data give the same information?? To me they dont.... Please help me understand this...

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              17G   14G  2.2G  86% /
varrun                499M  116K  499M   1% /var/run
varlock               499M     0  499M   0% /var/lock
udev                  499M   56K  499M   1% /dev
devshm                499M   92K  499M   1% /dev/shm
lrm                   499M   45M  455M   9% /lib/modules/2.6.24-24-generic/volatile
gvfs-fuse-daemon       17G   14G  2.2G  86% /home/manpreet/.gvfs

```PS also tell me how do i **mark a thread as solved**? The option is not there in **thread tools**

---

### Post by livestockPimp on 2009-05-26
at a guess the screenshot is talking about /dev/sda as a whole and the "df" is talking about your mounted partitions, ie; sda3 is 17GB but as a whole you have I am assuming a 40GB drive with 5gb free?

---

### Post by meet.aman7 on 2009-05-26
But i had only allocated 20 GB for ubuntu ->like the data says.

---

### Post by KhurramM on 2009-05-26
What exactly do u need to know.

Your ubuntu is on 17gb partition.

Cant say about other partitions.

Try gparted to have a clear picture, it will show u in graphics mode all the partitions, may be your problem will be solved.

---

### Post by meet.aman7 on 2009-05-26
My question is -- What is the image showing here and why is is different from the data?? because on the net other screenshots that isaw were consistent with the data and mine isn't  :confused:

PS also tell me how do i **mark a thread as solved**? The option is not there in [B]thread tools



[/B]

---

### Post by meet.aman7 on 2009-05-27
Common guys please help me here... dont let this go unanswered..

---

### Post by rudy.b on 2009-05-27
They are displaying different information.  The **df** command will display your root partition where Ubuntu is running while the Disk Usage Analyzer will display all mounted partitions.  My displays are different too, because I have two hard drives.  You must have another partition mounted that is being displayed in the Analyzer, but not in the df display.

And to mark a thread as "solved": I think you just edit the subject in the first post in the thread to add the text "[solved]" at the front.

---

