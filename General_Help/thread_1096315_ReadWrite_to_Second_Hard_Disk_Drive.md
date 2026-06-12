---
title: "Read/Write to Second Hard Disk Drive"
date: 2009-03-14
forum: General Help
---

### Post by Luke_Bachi on 2009-03-14
HI,

I am new to Linux and Ubuntu and do not have much knowledge on how the system works, thats why I am here becase I a totally lost!. 

Heres my problem...

I have installed a second hard drive as a slave to my master hard drive (I have Ubuntu 8.04 installed on my system. I used Gparted to partition my second hard drive to the "ext3" format. I now try and access this drive and it won't let me create folders or copy files to it. WHY!?!

It would be most appreciated if someone can help me with this problem.

Regards
Luke
[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by taurus on 2009-03-14
Where did you mount that second harddrive to, mount point?  Since it's ext3, all you need is to change the ownership of the mount point for that second harddrive from root to your login name.  Then, you should be able to write to it anytime you want.

Assuming the mount point is /media/sdb1 and your login name is luke, you would do

```
sudo chown -R luke:luke /media/sdb1
ls -la /media
```

---

### Post by blackened on 2009-03-14
Give this a read, should get you moving in the right direction:
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux").

---

### Post by Luke_Bachi on 2009-03-16
Hi again,

I still can't seem to get it to work. The PC can see the hard drive but when i click on it it says the following:

[I]Cannot Mount Volume.

Unable to mount the volume.

Details.
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)[/I]

Can you please help/advise as to how to correct this problem?

Thanks again 
Luke 

P.S. I am new to Ubuntu and am struggling with all of these command line based fixes. Isn't there a program or something that can fix this problem for mounting a Hard Disk drive?

Regards

---

### Post by ugm6hr on 2009-03-16
What have you named (labelled) the HD?

The reason I ask, is because Ubuntu defaults to mounting at /media/disk, but if the device has a label, it defaults to /media/*label*

It appears that it is trying to mount the HD to a disallowed location, which contains a / in the label, or perhaps is longer than 16 characters.

You can check with e2label (where *device* is probably sdb1 in your case, or possibly sda1, hda1, hdb1):
```
sudo e2label /dev/*device*
```

---

### Post by Luke_Bachi on 2009-03-19
Okay,

Thanks everyone for your help so far, I really appreciate, However I still cannot seem to "mount" the hard drive. This is really starting to s**t me! I must make a point now that I am new to Ubuntu and as such I am a total dunce! All of the terminal commands are very difficult to understand.

Let me put this simply. I have installed a second Hard drive on my Ubuntu PC. I want said hard drive to work on Ubuntu PC. It isn't working. How do I get Ubuntu to get it to work so that I can copy my files to it? Is it really this f*****g hard every time one installs a new piece of hardware?  I can now understand why Windows is so popular because stuff seems to always work when you plug it in...

Anyway about my hard drive; I have formatted it to ext3 as stated by the GParted Partition Manager Software.The Hard drive previously contained no errors or ever had any problems. 

If anyone can help tell me or tell me of a program I can use to setup my second hard drive on Ubuntu It would be very much appreciated!

Thanks 

Luke

---

### Post by ugm6hr on 2009-03-19
Unfortunately, reiterating the same information doesn't really help us to help you any further.

I understand that Terminal commands may be difficult to understand, but surely copy & paste is not so hard?

If you want info specific to your situation, start with:

```
sudo fdisk -l
```

Copy and paste into Terminal, and then copy and paste the output back here.

---

