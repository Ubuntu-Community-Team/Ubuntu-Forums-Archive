---
title: "Raid1 Reinstall"
date: 2009-01-27
forum: General Help
---

### Post by kfarrell on 2009-01-27
So I set up a raid1 array with /dev/sdb and /dev/sdc, I installed Ubuntu on /dev/sda.

I took the array out and plugged them into a different computer, but it has the same setup.

How can I get /dev/sdb and /dev/sdc seen on my new ubuntu install. I figure I have to point them to /dev/md0 somehow, just not sure how.

mdadm --examine /dev/sdb shows...

```
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e51ae197:88ee6966:d7cae86f:1e519c16
  Creation Time : Wed Jan 21 21:24:22 2009
     Raid Level : raid1
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Jan 27 22:06:41 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : db63ed03 - correct
         Events : 5
```

and /dev/sdc shows...

```
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e51ae197:88ee6966:d7cae86f:1e519c16
  Creation Time : Wed Jan 21 21:24:22 2009
     Raid Level : raid1
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Jan 27 22:06:41 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : db63ed11 - correct
         Events : 5
```

Thanks in advance.

---

### Post by fjgaude on 2009-01-27
I assume the array is being assembled at boot up.

First you make a mountpoint like so:

```
sudo mkdir /home/raid
```

Then you mount the array:

```
sudo mount /dev/md0 /home/raid
```

Of course you can make a mountpoint anywhere with any name you wish, I showed an example.

After that works for you, you can add a line in your /etc/fstab file so the array mounts automatically when you boot up.

Let us know how you are doing.

---

