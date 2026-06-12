---
title: "Unable to mount RAID Mirror"
date: 2009-04-07
forum: General Help
---

### Post by rkrueger on 2009-04-07
I just installed Ubuntu 8.10 desktop for the first time. I am a total Linux newb and I'm just glad that I'm up and running. I have an established mirror RAID on a pair of drives I use for storage/backup. The File Browser shows the two drives as separate drives and when I click on them, it says it is unable to mount.

I'm having a hard time trying to figure out how to get these drives recognized as a mirror raid and allow me to access them.

Also, how does one share a drive on the network?

-EDIT-

Let me clarify that this a BIOS raid established on a Highpoint RocketRaid card via SATA.

---

### Post by fjgaude on 2009-04-07
Well, you are in for a lot of learning... the program **dmraid** is what you need to do what you want. Take a look at these links:

[http://users.telenet.be/mydotcom/how...skfakeraid.htm](http://users.telenet.be/mydotcom/how...skfakeraid.htm)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Let us know how you are doing.

---

### Post by rkrueger on 2009-04-07
I will take a look into that app.  Thanks for the links, although the FakeRaid I did find before, it appears to be focused on how to get Ubuntu installed onto a RAID drive.

I'll get back after I play with dmraid.  Thanks!

---

### Post by rkrueger on 2009-04-07
Well, I got DMRAID installed and I've tried the following :

robert@Server:~$ sudo dmraid -r
/dev/sdb: isw, "isw_cifggjceag", GROUP, ok, 781422766 sectors, data@ 0
/dev/sda: via, "via_ccbhcjahfj", mirror, ok, 976773167 sectors, data@ 0


robert@Server:~$ sudo dmraid -a y
ERROR: creating degraded mirror mapping for "isw_cifggjceag_Stuff"
ERROR: creating degraded mirror mapping for "via_ccbhcjahfj"
robert@Server:~$ sudo dmraid -s
*** Group superset isw_cifggjceag
--> Subset
name   : isw_cifggjceag_Stuff
size   : 781422080
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 1
spares : 0
*** Set
name   : via_ccbhcjahfj
size   : 976773160
stride : 8
type   : mirror
status : ok
subsets: 0
devs   : 1
spares : 0



I don't want to lose the data that's already on these mirrored drives.

---

### Post by fjgaude on 2009-04-08
Gosh, I'm not much for dmraid... you have multiple partitions on the mirrored drives?

---

### Post by rkrueger on 2009-04-08
No. 

The mirrored drives are single partitions.

---

### Post by fjgaude on 2009-04-08
I guess dmraid thinks the partitions are not good. At least not mirrored in a way it knows how to put them back together.

```
sudo dmraid -ay
```

You can try to mount each one using the mapper way:

```
sudo mount -t ntfs /dev/mapper/isw_cifggjceag /mountpoint
```

And similarily for the other pair.

You know how to make a mountpoint?

---

