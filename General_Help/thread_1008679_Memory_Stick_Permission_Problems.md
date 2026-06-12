---
title: "Memory Stick Permission Problems"
date: 2008-12-11
forum: General Help
---

### Post by xXZeroXx on 2008-12-11
Lately I've had some problems with my psp and memory stick, I've never been able to mount my psp in a specific directory using fstab i.e. /media/psp so I discovered something I hadn't seen before if I clicked on properties over my memory stick it said volume and then mount options so I thought I would be able to mount it that way without using fstab, so I changed the mount options, but It just went worst since then, I couldn't even mount my psp, I went to Conf Editor and erased all values after that I was able to mount my psp again but surprise! I couldn't write anything, just read, because the owner of the memory stick is "root" I've tried with chown and chmod, but nothing happened, I've also tried to format it, but it remains the same, formatting (with gparted and psp) won't work, so I think I messed something up, any idea to become the owner of the memory stick again so I can write things on it?:confused:

Thanks for your help!:lolflag:

---

### Post by 2hot6ft2 on 2008-12-11
Back up whatever is on it. Stick it in a windows pc and format it. This worked for me with a sd card and usb reader that had the same problem.

Be sure to use the safely remove hardware in windows, down in the lower right by the clock before removing it or you'll have other issues.

---

### Post by albinootje on 2008-12-11
What filesystem did you use, and how do you want to use that usb-stick ?
FAT is an ancient filesystem, which needs more free space than most other filesystems (so you will lose a bit more free space), and it will let anyone write to it.

NTFS is not so ancient and much more sophisticated, and can handle permissions, but for usage in Linux it can be a little annoying when the NTFS filesystem is labeled "dirty" by MS-Windows.

With the Linux filesystems like ext2,ext3,xfs,jfs,reiserfs you are not allowed to write to it as normal user by default.

If you want to write to a filesystem from Linux as normal user you have at least two options :

1) mount it using relevant mount options for that, see : man mount
  (Relevant example options are "user" and "umask=000)
2) create a directory on the usb-disk, and make your normal user owner of that. For example : sudo mkdir /media/disk/mydata ; sudo chown username /media/disk/mydata

---

### Post by xXZeroXx on 2008-12-11
> What filesystem did you use, and how do you want to use that usb-stick ?
Filesystem is FAT and I want to use it for my psp, however I need to write things to it from my computer, and there is where the problem shows up, I can write things on it from Windows but not from Linux, and the problem is that I can't be rebooting all time just to write something on it.
The filesystem must be FAT32 in order to be read and used by the psp, but whenever I mount it, it says I've got no permissions and only root can write things on it. And even as a root user I can't change the owner of the memory stick.

---

### Post by albinootje on 2008-12-11
Hmm, weird, what about remounting it with the options user,umask=000 ?
For example, let's assume the usb-stick is /dev/sda1, and it is currently mounted at /media/disk

then try : 
sudo umount /media/disk
sudo mount /dev/sda1 /media/disk -o user,umask=000

---

### Post by xXZeroXx on 2008-12-11
> **albinootje said:**
> Hmm, weird, what about remounting it with the options user,umask=000 ?
For example, let's assume the usb-stick is /dev/sda1, and it is currently mounted at /media/disk

then try : 
sudo umount /media/disk
sudo mount /dev/sda1 /media/disk -o user,umask=000

No luck, it says the owner is still root, I can erase things from it but I can't write things on it.

---

### Post by theozzlives on 2008-12-11
```
sudo chown  user /media/psp
```

---

### Post by xXZeroXx on 2008-12-11
> **theozzlives said:**
> ```
sudo chown  user /media/psp
```

It says that the operation is not allowed.
Any other idea:confused:

---

### Post by Eviltechie on 2008-12-11
You could try re-partitioning it with gparted.

---

### Post by Chunky Dunk on 2008-12-12
Can you mount it as a regular user (i.e. plugging it in while logged in as a user and have it auto-mounted). FAT systems usually belong to who ever mounts them. Thats why using the sudo command results in it being owned by root.

---

### Post by xXZeroXx on 2008-12-12
> **Eviltechie said:**
> You could try re-partitioning it with gparted.

How to do that?

> **Chunky Dunk said:**
> Can you mount it as a regular user (i.e. plugging it in while logged in as a user and have it auto-mounted). FAT systems usually belong to who ever mounts them. Thats why using the sudo command results in it being owned by root.

When I enter into my sessions as user (xxzeroxx) and I put the memory stick inside my psp and then I plug my psp into my pc via USB cable, it mounts automatically, but when I try to write something to it, it says I don't have enough permission, I almost never mount things with sudo, they always get auto-mounted when I plug them in.

---

### Post by xXZeroXx on 2008-12-13
Is there anything I can do?
I've reinstalled ubuntu (well actually upgraded from 8.04 to 8.10) but the problem remains there, something at /home I should erase, please help :frown: T_T

---

### Post by albinootje on 2008-12-14
Do you have the same problem with other usb-sticks ?
And can you clarify the "something at /home I should erase" ?

---

### Post by xXZeroXx on 2008-12-14
> **albinootje said:**
> Do you have the same problem with other usb-sticks ?
And can you clarify the "something at /home I should erase" ?

No, just this memory stick, my other memory stick is OK and my usb-sticks are ok too. "something at /home i should erase" I mean, when you install something your preferences are saved in /home/user/.xxx where "xxx" is the name of the program you installed, I was wondering if this "preference" (where and how to mount memory stick) was saved in here, if thats the case maybe I just should erase the .xxx thing.

---

### Post by albinootje on 2008-12-14
Good to hear that you don't have problems with other usb-sticks!

And i think it's not possible to delete certain user preferences to make this one usb-stick mount read/write.

---

### Post by xXZeroXx on 2008-12-14
> **albinootje said:**
> Good to hear that you don't have problems with other usb-sticks!

And i think it's not possible to delete certain user preferences to make this one usb-stick mount read/write.

So.... What do I do now?

---

### Post by albinootje on 2008-12-14
I've ran out of ideas, sorry, I don't know :(

---

### Post by xXZeroXx on 2008-12-18
> **2hot6ft2 said:**
> Back up whatever is on it. Stick it in a windows pc and format it. This worked for me with a sd card and usb reader that had the same problem.

Be sure to use the safely remove hardware in windows, down in the lower right by the clock before removing it or you'll have other issues.

No, it did not help. Please any other suggestions?

---

### Post by xXZeroXx on 2008-12-31
People thanks for your support, but I couldn't solve the problem, so I give up, I'm leaving linux and going back to windows, "why?" you ask, because I have no problems with windows, a good anti-virus and an anti-spyware and then it's done, I'll miss linux, but I can't be living like this, there's always a problem here, the sound, the graphics card,the usb, the hdd, so... I'm done, I might come back in the future but, for now, windows 7 looks good as far as I have tested inside the beta. So, good bye my friends, and I hope to see you again soon.:popcorn:
PD: If anyone finds the solution to this problem please post it or PM me. 
Thanks for all :D

EDIT: I'm back! I had to format everything in order to solve the problem, but I'm back, and I'm happy about it, hope to help you guys out.

---

