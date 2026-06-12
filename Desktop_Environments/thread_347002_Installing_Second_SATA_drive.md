---
title: "Installing Second SATA drive"
date: 2007-01-26
forum: Desktop Environments
---

### Post by edward4130 on 2007-01-26
Here is the situation:
I have  500GB SATA with Edgy Running, and a second IDE320GB that I mounted Extra.  Works fine but change was emminent as I got a good deal on another 500SATA.  The IDE is comming out (it's backed up) and I'm putting in the SATA.  I got this 2 drive thing to happen before by installing a full version of ubuntu on the IDE even though it was a second drive.  When I removed everything but /home on it (root: rm -rf *.*), the system will go to grub and ask to boot from it (bootstrap?)...Obviously it can't, I deleted it all!!   I dont want any system on it this time but still have to formatt it somehow, I only want clear space and files on the new one.

Now what do I do in fdisk?....Or is there a Drive utility for Gnome that I can't seem to locate?

I need the new SATA 500 to be:
formatted clean
non-booting
one big partition

Once it is in I will mount it in /dev for mythtv to use or I will make it my archive for everything the I process out of mythtv to divx.
-Edward
Thanks in advance for the direction :)

---

### Post by uNiverSus on 2007-01-26
i got almost the same problem ;/ ive got one hard drive with 60GB ( linux on it ) and a new drive 80 GB ( formated in gparted ) , its a one big partition and i can't mount it ;/ Only errors dunno why ;(  Life is brutal my friend ;/

---

### Post by taurus on 2007-01-26
> **uNiverSus said:**
> i got almost the same problem ;/ ive got one hard drive with 60GB ( linux on it ) and a new drive 80 GB ( formated in gparted ) , its a one big partition and i can't mount it ;/ Only errors dunno why ;(  Life is brutal my friend ;/

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by uNiverSus on 2007-01-27
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
Code:

sudo fdisk -l

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

that all i get when i use sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9964    80035798+  83  Linux

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7289    58548861   83  Linux
/dev/hdb2            7290        7476     1502077+   5  Extended
/dev/hdb5            7290        7476     1502046   82  Linux swap / Solaris

---

### Post by taurus on 2007-01-27
> **uNiverSus said:**
> that all i get when i use sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9964    80035798+  83  Linux

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7289    58548861   83  Linux
/dev/hdb2            7290        7476     1502077+   5  Extended
/dev/hdb5            7290        7476     1502046   82  Linux swap / Solaris

So you want to mount /dev/sda1.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add the following line to the end of it.

```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

### Post by uNiverSus on 2007-01-27
> So you want to mount /dev/sda1. Edit /etc/fstab

Code:

gksudo gedit /etc/fstab

and add the following line to the end of it.

Code:

/dev/sda1 /media/sda1 ext3 defaults 0 1

Save it. Then, create a new mount point and mount it.

Code:

sudo mkdir /media/sda1 sudo mount -a df -h



Big thx for help . It works but i got a next problem ;/  On sda1 there is only a folder lost+found. The major problem is now that i cant write on the drive ;/ I hope u understand me . 

Hope this screenshot wills how u what i mean [[IMG]http://img261.imageshack.us/img261/9020/screenshotlv0.th.png[/IMG]](http://img261.imageshack.us/my.php?image=screenshotlv0.png)

---

### Post by taurus on 2007-01-27
Okay, so you want to be able to write to /media/sda1.  Just change the owner of /media/sda1 from root to your login name, **orion**, and you are all set.

Applications -> Accessories -> Terminal
```
sudo chown -R **orion**:**orion** /media/sda1
ls -la /media
```

---

### Post by uNiverSus on 2007-01-27
> Okay, so you want to be able to write to /media/sda1. Just change the owner of /media/sda1 from root to your login name, orion, and you are all set.

Applications -> Accessories -> Terminal
Code:

sudo chown -R orion:orion /media/sda1 ls -la /media



BIG THX IT WORKS FINE :* . Thank you very much . You are the best !

---

### Post by edward4130 on 2007-01-27
Ok did not reallly get any answer so I'm working this whole system from scratch, and hoping to jsut move some data back over to the new drive.  Now I realize that Grub was on the IDE driv e now I have reinstalled ubuntu on the newest SATA three times attmpting to get the propper setting for Grub because it sets default to [COLOR="Red"]hd0[/COLOR], now we know that I dont have any drive in there that will be hd-anything.

Was I correct in setting the Grub to be on (sda)?  I tried (sd0) and (sd1)  but nothing would boot without a live CD put back in, and no... I can't put the IDE back in.  The point is to have the two SATA's

Another hope is to load Grub on to the second SATA, it already has a full filesystem and even my working mythtv on it.  It would be wonderfull to just reset it to boot from it automaticly but the instructions are all about "hd..." and when I tried to put in sda stuff it just kept erroring in the grub prompt.

-Edward

Please help guys, this thread got accidently hijacked by another problem.  I still need help...THX!

---

### Post by edward4130 on 2007-01-27
Nope (sda) doesn't work... he he it crashes the installer!

Ok guys let me know I can't seem to find the documentation on this.

-Edward

---

### Post by edward4130 on 2007-01-27
Alright folks!! My system is totaly FUBAR!!!

All I can find is tutorials that are vague as hell and all about dual booting and stuff.  I dont want or have anything to do with windoze!!  All I have is this.

sata sda jsut installed but wont boot
sata sdb with full system on it wont boot

IDE now gone that had a system on it but now I cant get GRUB on anything.. Please somone help.

---

### Post by edward4130 on 2007-01-28
got it figured out with this link... thanks guys we got it done .. whew!

[http://www.ubuntuforums.org/showthread.php?t=224351]("http://www.ubuntuforums.org/showthread.php?t=224351")

---

### Post by edward4130 on 2007-02-01
Ok the help in theis did not work quite the way I needed it to.  Now I rebuilt the full system and adding a second sata drive  Here is the fdisk list:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60448   485548528+  83  Linux
/dev/sda2           60449       60801     2835472+   5  Extended
/dev/sda5           60449       60801     2835441   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60448   485548528+  83  Linux
/dev/sdb2           60449       60801     2835472+   5  Extended
/dev/sdb5           60449       60801     2835441   82  Linux swap / Solaris

```
/
I added this to my /etc/fstab but get an invalid filesystem.... WTF?!?!

```
/dev/sdb1   /media/WD500  linux   defaults   0   1
```

 I hope someone can help I spend hours finding other ways around.  My mythtv works on 111one system but the tv out and so on works on the other, but now I cant get the second to mount.  THERE IS NOT ANY TUTORIAL WORTH A DARN ON THIS!!!  ALL are about dual booting and stuff  I don't want Windoze!!! 

-Edward

---

### Post by edward4130 on 2007-02-01
sorry that line was Linux capital "L" 

-Ed

---

### Post by taurus on 2007-02-01
It should be

```

/dev/sdb1   /media/WD500  **ext3**  defaults   0   1

```

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by edward4130 on 2007-03-15
Thanks. I ended up using a third harddrive that was an IDE and put the Ubuntu OS on it and the two SATA drives are for storage of Mythtv files.  It seems that even when set up propperly I could not get multiple SATA drives working, only one at a time.  When the primary is at problems, avoided solving the problem by spending more money.

-Edward

---

