---
title: "[SOLVED] how to read root.disk"
date: 2008-12-09
forum: General Help
---

### Post by untappedpilot2 on 2008-12-09
I ruined my laptop but I still have the hard drive. The new desktop I'm using has just Xubuntu on it. When I first installed Linux on my laptop I was still using Windows XP. So I used Wubi to install Xubuntu. I just recently bought an adapter that allows me to  plug my laptop hard drive into my desktop pc. From what I can tell Wubi stores its information in this root.disk folder. I'm trying to retrieve the information from my old laptop but all I can see is my old Windows partition. I think I need a way to read this root.disk  How would I go about doing this?

---

### Post by Jammanuser on 2008-12-09
> **untappedpilot2 said:**
> I ruined my laptop but I still have the hard drive. The new desktop I'm using has just Xubuntu on it. When I first installed Linux on my laptop I was still using Windows XP. So I used Wubi to install Xubuntu. I just recently bought an adapter that allows me to  plug my laptop hard drive into my desktop pc. From what I can tell Wubi stores its information in this root.disk folder. I'm trying to retrieve the information from my old laptop but all I can see is my old Windows partition. I think I need a way to read this root.disk  How would I go about doing this?

You need to first mount the root.disk using a Ubuntu LiveCD in order to recover ur files!

For detailed instructions on how to do this, see: [http://ubuntuforums.org/showthread.php?t=1000370](http://ubuntuforums.org/showthread.php?t=1000370)

That's a thread that i started in order to help people like u mount the root.disk to recover data from after Wubi fails! :D

Cheers! ):P

-jammanuser

:guitar:

---

### Post by untappedpilot2 on 2008-12-11
So I'm still having a little bit of trouble here... I'm trying to mount the root.disk file on my external hard drive. And I need to use a LiveCD to do this? I can't just use my existing Xubuntu installation? Do I need the device name? If so how to I tell what it is? When Xubuntu auto mounts my external drive I can get to it through /media/disk. I made a /vdisk folder in the /(root) folder and tried: 

```
sudo mount -o /media/disk/ubuntu/disks/root.disk /vdisk
```
and i got...
 ```
mount: can't find /vdisk in /etc/fstab or /etc/mtab
```

What's going on here? Do I need to copy my root.disk file to my hard drive?

---

### Post by Jammanuser on 2008-12-11
> **untappedpilot2 said:**
> So I'm still having a little bit of trouble here... I'm trying to mount the root.disk file on my external hard drive. A**nd I need to use a LiveCD to do this? I can't just use my existing Xubuntu installation?** Do I need the device name? If so how to I tell what it is? When Xubuntu auto mounts my external drive I can get to it through /media/disk. I made a /vdisk folder in the /(root) folder and tried: 

```
sudo mount -o /media/disk/ubuntu/disks/root.disk /vdisk
```
and i got...
 ```
mount: can't find /vdisk in /etc/fstab or /etc/mtab
```

What's going on here? Do I need to copy my root.disk file to my hard drive?

ok...i guess that changes things a bit in ur case, since ur using an external hard drive, and can get into ur Xubuntu installation! to answer ur question whether u can mount the root.disk from Xubuntu: the answer is YES! ;) obviously though, that changes things a little bit, so instead of running:

```
sudo mkdir /win
**sudo mount /dev/sda3** 

```
ur going to have to sudo mount it with the correct name, i.e. instead of "sda3", use whichever code would be appropriate in ur case! since a=disk and 3=partition, urs will probably be something like:

```
sudo mount /dev/sdb1 /win
```

and then if that works u can continue with the rest of the commands, as normal:

```
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

Let me know if it works or not! ;)

Cheers! ):P

-jamman

:guitar:

---

### Post by Jammanuser on 2008-12-11
> **untappedpilot2 said:**
> 
What's going on here? Do I need to copy my root.disk file to my hard drive?

Copying ur root.disk to ur **internal** hard drive will also work...though you'll first have to put it in ur "disks" folder in C:/ubuntu/disks on Windows... ;)

Cheers! ):P

-Jam Man

:guitar:

---

### Post by untappedpilot2 on 2008-12-12
I think copying it to the internal hard drive would be the way to go.. now I don't know if you've caught this but I'm no longer using a Wubi installation. The external hard drive is an adapter for my laptop hard drive with my old Windows installation / Wubi so on an so forth. My new computer is straight Xubuntu and was installed without Wubi. So if I copy it to my internal hard drive where would I put it?

---

### Post by Jammanuser on 2008-12-12
> **untappedpilot2 said:**
> I think copying it to the internal hard drive would be the way to go.. [COLOR="Red"]now I don't know if you've caught this but I'm no longer using a Wubi installation[/COLOR]. The external hard drive is an adapter for my laptop hard drive with my old Windows installation / Wubi so on an so forth. My new computer is straight Xubuntu and was installed without Wubi. So if I copy it to my internal hard drive where would I put it?

oh...so ur using a **real** install now! no...i don't believe u mentioned that before! i'm pretty sure u said that Xubuntu was installed with Wubi, in ur first post...

but anyway, i think u could easily access the root.disk even though its on a original laptop drive, instead of a usual external HDD, because its connected as one! but if u insist on moving it to ur internal HDD...

Then u can simply move it into ur Xubuntu installation, into whatever folder u want, and then mount the root.disk from Xubuntu itself...using the following command with the appropriate file names:

```
sudo -o loop **/win/ubuntu/disks/**root.disk /vdisk
```

However, since i have never actually mounted the root.disk this way before, i.e. from a Xubuntu installation, and mounting a root.disk from Xubuntu itself, i can only guess on the procedure...u may have to first create a /win and /vdisk folders and mount /win before mounting the root.disk...

In that case, precede the above command by the following ones: 

```
sudo mkdir /win
sudo mount /dev/**sda1** /win
sudo mkdir /vdisk

```
Of course, as always, replace "sda1" with the appropriate configuration, i.e. "sda2" or "sda3"... 

just remember: a=disk, 1=partition number

GD and let me know how it goes! ):P

Cheers! :)

Jam Man

:popcorn:

---

### Post by untappedpilot2 on 2008-12-13
ok.. with you so far. I'm just not sure how to tell which what the "sda1" needs to be replaced with. Is there a command I can do to list the HDD connected to my computer with their respective names? Even if I move my root.disk file to my internal HDD I"m not sure how to tell which one it is. I would guess it is "sda1" since it would logically be the first drive and the sole partition on it.

---

### Post by Jammanuser on 2008-12-13
> **untappedpilot2 said:**
> ok.. with you so far. I'm just not sure how to tell which what the "sda1" needs to be replaced with. Is there a command I can do to list the HDD connected to my computer with their respective names? Even if I move my root.disk file to my internal HDD I"m not sure how to tell which one it is. [COLOR="Red"]I would guess it is "sda1" since it would logically be the first drive and the sole partition on it.[/COLOR]

Indeed...so first try that to see if its the right one! my guess is it is! and then we can work from there, if it doesn't work...but **first** try it! ;) Don't worry...if its the wrong one, it wont screw up anything! it'll just give u a message saying it no such file or directory exists...no harm in trying! :D

Cheers! ):P

Jam Man

:guitar:

---

### Post by untappedpilot2 on 2008-12-14
Okay, So as I expected this is the error I'm getting.

```
/win/ubuntu/disks/root.disk: No such file or directory

```

Moving the file from my external HDD really isn't an option for me because the file is simply too large. So how do I figure out what to replace "sda1" with to signal the external HDD. When I looked through my /dev folder there were multiple sda1, sdc1, and so on. How do I determine which of those is the external HDD?

---

### Post by untappedpilot2 on 2008-12-14
Also here's my output for : 

```
sudo fdisk -l
```


desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986   83  Linux
/dev/sda2            2340        2431      738990    5  Extended
/dev/sda5            2340        2431      738958+  82  Linux swap / Solaris

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
64 heads, 32 sectors/track, 28615 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          48       48163+  de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sdc2   *          48       25024    25575480    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdc3           25024       28608     3670852+  db  CP/M / CTOS / ...
Partition 3 does not end on cylinder boundary.

=====================

So I'm guessing my externall HDD is the /dev/sdc2 because that is the installation that still has Windows and Xubuntu installed through Wubi. (And the root.disk file!) I'm pretty sure that's it because it shows its a 26GB drive on my desktop. What do you think? Assuming it's correct to mount the drive I do:

```

sudo mount /dev/sdc2 /win
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

```

then everything should be in the /vdisk folder right?

---

### Post by Jammanuser on 2008-12-14
> **untappedpilot2 said:**
> Okay, So as I expected this is the error I'm getting.

```
/win/ubuntu/disks/root.disk: No such file or directory

```

[COLOR="Red"]Moving the file from my external HDD really isn't an option for me because the file is simply too large.[/COLOR] So how do I figure out what to replace "sda1" with to signal the external HDD. When I looked through my /dev folder there were multiple sda1, sdc1, and so on. How do I determine which of those is the external HDD?

Well...that would have been certainly nice to know before! now u have me jumping back and forth between the proceedures to mount the root.disk on the **internal** and the **external** drives! :rolleyes: So u say u want to mount it, while its on the **external** drive? in that case, just go with the proceedure outlined above for the external drive! ^ however, since it sounds like (in ur case) it might be "sdc2" instead of "sdb1", make sure to do that in place of "sdb1"! ;)

Let me know if it works or not! ):P

Cheers! :p

Jam Man

:guitar:

---

### Post by untappedpilot2 on 2008-12-14
Actually I just went ahead and tried it and everything worked out at last!! Many thanks for your patience and help!

---

### Post by Jammanuser on 2008-12-14
> **untappedpilot2 said:**
> Also here's my output for : 

```
sudo fdisk -l
```


desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986   83  Linux
/dev/sda2            2340        2431      738990    5  Extended
/dev/sda5            2340        2431      738958+  82  Linux swap / Solaris

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
64 heads, 32 sectors/track, 28615 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          48       48163+  de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sdc2   *          48       25024    25575480    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdc3           25024       28608     3670852+  db  CP/M / CTOS / ...
Partition 3 does not end on cylinder boundary.

=====================

So I'm guessing my externall HDD is the /dev/sdc2 because that is the installation that still has Windows and Xubuntu installed through Wubi. (And the root.disk file!) I'm pretty sure that's it because it shows its a 26GB drive on my desktop. What do you think? Assuming it's correct to mount the drive I do:

```

sudo mount /dev/sdc2 /win
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

```

then everything should be in the /vdisk folder right?

Ok...hmm...it does indeed sound like (like u just said!) that ur external drive is "sdc2"! so i just modified my above post, to say that instead of "sdc1"! also...before u can run the commands u listed, u first have to create the "/win" and "/vdisk" folders, in order to mount them! ;)

In order to do this, simply do:

sudo mkdir /win

This will of course create the "/win" folder...and next run the first command u mention, i.e. "sudo mount /dev/sdc2 /win"
And then proceed to do:

sudo mkdir /vdisk

And then finally u can run ur last command! :p

Cheers! ):P

Jam Man

:popcorn:

---

### Post by Jammanuser on 2008-12-14
> **untappedpilot2 said:**
> Actually I just went ahead and tried it and everything worked out at last!! Many thanks for your patience and help!

Ok...cool! :D in that case, ignore my **last** post!

I'm glad i could help! ):P

Cheers! :p

Jam Man

:guitar:

---

