---
title: "can't see hard drive in LiveCD, can't see USB in rescue"
date: 2009-05-05
forum: General Help
---

### Post by rlb.contact on 2009-05-05
Hi,
At this point, I really don't care about saving the install. I don't care one bit except for the data in my home/user files.

I can used the LiveCD to boot up, and I can access my USB drives. However, I cannot see my hard drive or any of its partitions. I try to force a mount, but I get an error message saying that these are not found in fstab or mtab.

I'll boot to recovery mode on the hardrive itself. I can get to the root shell without a problem. I can see, and enter my hardrive. However, I cannot get my usb drives to mount. If I could I would just move the /home/directories wholesale to my external USB drive and be done with it all.

Any Ideas?
Thanks,
Lee

---

### Post by tjwoosta on 2009-05-05
on live cd run this command to find the name of the drive that your trying to mount
```
sudo fdisk -l
```
you sould see something like this
```

/dev/sda1   *           1        7110    57109504    7  HPFS/NTFS
/dev/sda2            7111        7483     2996122+  82  Linux swap / Solaris
/dev/sda3            7484       14593    57111075   83  Linux

```

now do
```
sudo mkdir /media/mountdisk
```
(this will simply create a new folder called mountdisk located in /media, you can actually use any name you want but mountdisk sounds good to me)

now depending on whatever disk you want to mount do
```
sudo mount /dev/whateverdisk /media/mountdisk
```
(this will mount the disk and display the contents in the /media/mountdisk folder)

for instance if i wanted to mount my linux partition "sda3" i would do this
```
sudo mount /dev/sda3 /media/mountdisk
```

if you ever want to unmount the partition just do this
```
sudo umount /media/mountdisk
```
(thats not a typo, its "umount" not "unmount")

or you could just shutdown and it will unmount automatically anyway

---

### Post by C0NSTANTIN on 2009-06-20
sudo fdisk -l >>>> does nothing
sudo mkdir /madia/mountdisk >>>> does nothing
sudo mount /dev/sda0 media/mountdisk>>>>> "mount: mount point media/mountdisk does not exist


i don't care about my data anymore .... i just want to install that OS !
[http://ubuntuforums.org/showthread.php?t=1192050](http://ubuntuforums.org/showthread.php?t=1192050)

---

### Post by tjwoosta on 2009-06-20
> sudo fdisk -l >>>> does nothing

? This should list all your hard disks, the only thing I can think of is that you must be doing something wrong. Did you copy and paste the command?

> sudo mkdir /madia/mountdisk >>>> does nothing

That should be media not madia, but anyway this should make a directory inside the media directory called mountdisk, you would be using that as your mount point.  (technially you could use any directory you want as the mount point just modify step 3 to coincide) 

If you are using the live cd the directory you make will disapear when you reboot, so you would want to do all of theese steps on one boot.

> sudo mount /dev/sda0 media/mountdisk>>>>> "mount: mount point media/mountdisk does not exist

Thats because something went wrong with step 2.

After sucessfully mounting the drive to your mount point you would simply navigate to the specified mount point directory to see all the files that are on the drive.


> i don't care about my data anymore .... i just want to install that OS !
[http://ubuntuforums.org/showthread.php?t=1192050](http://ubuntuforums.org/showthread.php?t=1192050)


The only thing I can think of is that there must be some stupidly simple things that are being overlooked or misunderstood.  Without actually being there and seeing what your doing and how things are set up its hard to specualte as to what is happening or how to correct the issues.


If you dont care about anything thats on the drive, just open the partition editor from the live cd (better off with this partitioner then the windows one) and delete everything on that drive, leave the space unallocated.


Pop in the live cd and go through the install process like normal.

Also if the installer gives you a choice, you would be much better off with ext3 then ext4.

---

### Post by C0NSTANTIN on 2009-06-21
> **tjwoosta said:**
> ? This should list all your hard disks, the only thing I can think of is that you must be doing something wrong. Did you copy and paste the command?



That should be media not madia, but anyway this should make a directory inside the media directory called mountdisk, you would be using that as your mount point.  (technially you could use any directory you want as the mount point just modify step 3 to coincide) 

If you are using the live cd the directory you make will disapear when you reboot, so you would want to do all of theese steps on one boot.



Thats because something went wrong with step 2.

After sucessfully mounting the drive to your mount point you would simply navigate to the specified mount point directory to see all the files that are on the drive.





The only thing I can think of is that there must be some stupidly simple things that are being overlooked or misunderstood.  Without actually being there and seeing what your doing and how things are set up its hard to specualte as to what is happening or how to correct the issues.


If you dont care about anything thats on the drive, just open the partition editor from the live cd (better off with this partitioner then the windows one) and delete everything on that drive, leave the space unallocated.


Pop in the live cd and go through the install process like normal.

Also if the installer gives you a choice, you would be much better off with ext3 then ext4.

i've loaded some terminal outputs of some commands i was sugested. I got showing in the terminal that SRST failed error that i receive when i boot ... 
[http://ubuntuforums.org/showpost.php?p=7492914&postcount=18](http://ubuntuforums.org/showpost.php?p=7492914&postcount=18)

i can't install xubuntu because ... i think ... mbs is busted ..
i think linux and windows have different sectors for the mbs cuz' windows can see my HDD
i can't use partitioners because they don't reach the lower data levels like MHDD does.
I got MHDD up and running unto a live CD i burned last night but i can't figgure out what inputs i should use ... and that "RANDOMBAD" input gives me the chills ... i'm using MHDD like a anti-tero disarming a bomb ...

---

### Post by kgkicker on 2010-10-24
I just installed XUBUNTU onto an 8GB flash drive with a 4MB of that persistent using Universal USB Installer.  I couldn't see the hard drive.  Your instructions (3 command line instructions) worked perfectly.  Might write a script to do this every time.  Thanks!

---

