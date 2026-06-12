---
title: "How to install ubuntu........."
date: 2008-12-17
forum: General Help
---

### Post by mahela007 on 2008-12-17
I have a 160 GB hard disk of which 80 GB is already full of windows. The rest is unpartitioned free space. Which option should I select during ubuntu installation to install ubuntu on the remaining disk space?
I tried selecting largest continuous free space but the before and after meters showed ubuntu being installed on the entire hard drive. Can someone help?
The screen shot attached is the screen I got when I selected "free space" in the installation menu

---

### Post by night_fox on 2008-12-17
That one should do. Ubuntu might automatically decide how to split up the rest of it. Just so you know, you dont make any changes to your hard disk until you have finished choosing all the settings, such as your own username, password, and computer name.

In case it doesn't do this,
Use about 2 Gb of swap space and make the rest ext3, mount point should be /

If you intend to install other linuxes in the future, make a separate tiny partition for /boot (50 megabytes say) and a separate partition for /home (as large as possible). make the / partition 10Gb. This is a rough guide. It means that all future linuxes you might have can share a common /boot and a common /home, so your files will be common to both and they will both update the same bootloader.

---

### Post by aheckler on 2008-12-17
Hmm, that is odd. It looks like the partitioner isn't detecting the Windows space and so wants to install itself on the whole drive, which it erroneously thinks is entirely empty. I'm not sure if that is normal behavior for the partitioner.

To be safe, you might just go with "Manual" and then put Ubuntu on the empty half of the disk. Maybe see what the partitioner thinks about that before installing.

---

### Post by mahela007 on 2008-12-17
> **night_fox said:**
> That one should do. Ubuntu might automatically decide how to split up the rest of it. Just so you know, you dont make any changes to your hard disk until you have finished choosing all the settings, such as your own username, password, and computer name.

In case it doesn't do this,
Use about 2 Gb of swap space and make the rest ext3, mount point should be /

If you intend to install other linuxes in the future, make a separate tiny partition for /boot (50 megabytes say) and a separate partition for /home (as large as possible). make the / partition 10Gb. This is a rough guide. It means that all future linuxes you might have can share a common /boot and a common /home, so your files will be common to both and they will both update the same bootloader.
"that one" meaning "continuous free space?"

---

### Post by mahela007 on 2008-12-17
> **aheckler said:**
> Hmm, that is odd. It looks like the partitioner isn't detecting the Windows space and so wants to install itself on the whole drive, which it erroneously thinks is entirely empty. I'm not sure if that is normal behavior for the partitioner.

To be safe, you might just go with "Manual" and then put Ubuntu on the empty half of the disk. Maybe see what the partitioner thinks about that before installing.
when I select manual the Windows partition shows up in green on the indicator. Doesnt it also show up in the screenshot? (the "before" indicator shows some partitioned space)

---

### Post by aheckler on 2008-12-17
Yeah the Before indicator shows Windows there, but then the After indicator shows Ubuntu using 100% of the drive, which is not what you want. You want it split 50-50.

Why it's like this even when you chose "Use largest contiguous free space" is weird.

---

### Post by mahela007 on 2008-12-17
I'm not very comfortable with the manual partitioning. Can you give me some instructions? More specifically I don't know about mount point and swap partitions

---

### Post by albinootje on 2008-12-17
> **mahela007 said:**
> I'm not very comfortable with the manual partitioning. Can you give me some instructions? More specifically I don't know about mount point and swap partitions

Can you choose the "guided - resize" (2nd) option, and make a screenshot of what shows up there ?

---

### Post by Vista1330 on 2008-12-17
Lets start from the beginning:
I understand u have Windows installed on ur system?
Just use teh windows disk partitioner to create a empty partition, u can even specify how large u want this partition to be: 72Gb right?
Now you created a new partition where Ubuntu will be installed.
Restart your PC with the Ubuntu disk inserted and when u get the options discribed above chose Use Largest continous space. Dont worry about Ubuntu telling u that 100% of the diskspace will be used just press forward and enter all teh requered spaces. After the installation all will be good;)

P.S. I did that when installing my copy of Ubuntu 8.10 and evrything worked perfectly fine

---

