---
title: "Partimage help!"
date: 2009-06-10
forum: General Help
---

### Post by Vizithor on 2009-06-10
HI!, I need make a image of one partition of my HHDD. 

My disk:
sda1--Win
sda2--NTFS
sda4--extended
sda5--Ubuntu
sda6--Others Linux
sda7--Swap
sda8--NTFS
sda9--NTFS

The idea is save sda5 in a image on sda9 (storage partition), for do this I use a LiveCD Linux with Partimage included. 
First I create ( mkdir /mnt/mydir ) in this step I can chage the attributes with CHMOD command, but when I mount sda9 in /mnt/mydir the folder become on "only read files" and CHMOD command not work of course Partimage can not save it and show me this message:

"Cannot Created Tempfile
[/mnt/mydir/SYSTEM-LOCAL/Pi3a5fd1d8.tmp]
Please, check there is space enough and you 
have acces rights."

*SYSTEM-LOCAL is a folder inside sda9 for images S.O only than I use*
Somebody can help me, I want save in a image, Ibex system before jump to Jackalope, I don´t want lose it. Also I treated with the Ghost in a Hiren´s Tool CD but not recognize the partitions, only is able C:\ (sda1). I´ll be grateful for any help.

---

### Post by unutbu on 2009-06-10
Instead of using Partimage, perhaps install Jaunty on sda9, leaving your other partitions, including sda5 untouched. That way, you will be able to checkout Jaunty and still be able to boot your current Ubuntu. 

If you really do want to use Partimage, however, perhaps the problem is a matter of permissions. Are you running "sudo partimage" so partimage is run with root privileges?

---

### Post by Vizithor on 2009-06-10
I know it is a permission problem, but, how I can changed, if CHMOD not work after mount sda9. Also I have sda6 to install Jaunty but I use this partition to test others Linux, in this moment I have install Sabayon4, and when I try to use partimage (as root)  to make a image of sda5 have a same problem of permission. Is like from Sabayon4 or LiveCD Partimage lose permissions to write even I how root.

---

### Post by unutbu on 2009-06-10
Please post the output of 
```

mount
cat /etc/fstab

```

---

### Post by TrakerJon on 2009-06-10
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by lewac on 2009-06-17
the problem is you are attempting to retain an image to a ntfs partition. to do that something "extra" is required. do this from a terminal:

blkid (to id your partitions. sometimes they differ so make note of the assignments) then...
mkdir /image
mount -t ntfs-3g /dev/sda9 /image
partimage (to launch partimage... at the 1st stem select your source partition and tab out to the 2nd step then do something like this at the destination):
/image/nameOfYourImageFile...

continuing F5's and you will receive a warning about access to ntfs partitions denoting "Experimenta1"!. however note that we've successfully recovered a number of images relating to ntfs with no known issues. and we've not had a failure.

to avoid this though you may wanna resize one of the lesser important ntfs partitions.. (using qtparted or some other partitioning package) and create an ext3 partition to retain your images on. one advantage of that is that windoze does not "see" ext3 at all.. the other advantage is that you avoid the "Experimental" warning on the write side.

---

