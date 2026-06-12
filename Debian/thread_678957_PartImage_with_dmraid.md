---
title: "PartImage with dmraid?"
date: 2008-01-26
forum: Debian
---

### Post by XtremeGamer99 on 2008-01-26
I somehow messed up my Debian a few days ago to the point where it wouldn't boot. I tried and tried but just couldn't recover anything, and so I decided to just reinstall. I didn't have anything important on it yet, except configuration files, so it wasn't a big loss.

But I'm trying to avoid something like that from happening again. I've been looking into it, and PartImage seems to be just what I need.

However, it doesn't seem to support dmraid. When I start it, it shows partitions not in any RAID configuration. 

I have two 160GB Hitachi SATA HDDs set up in a RAID0 configuration for a total of about 306GB.

I used dmraid when installing my Debian Lenny, and my RAID volume is mapped to /dev/mapper/isw_ceeihadafd_MyVolume

The first partition is my Windows XP partition. It starts at the beginning of the volume, taking 120GB with it. Then I have about 93GB of free space, then a 2.4GB extented filesystem with 54MB of free space and the rest going to swap (fifth patition, I dunno why I have free space with it). At the very end of the volume comes my Linux partition (second partition), with 91GB of space.

Here's a picture of GParted documenting my RAID volume in full. I've also got the device drop-down activated to show the different devices; sda and sdb are the physical HDDs, with the /dev/mapper/... are the RAID volumes and partitions.
[IMG]http://i82.photobucket.com/albums/j255/XtremeGamer99/screen.jpg[/IMG]

Now that I have my partition layout explained, let me explain the problem. I don't think PartImage is working with dmraid. Every time I start PartImage, it gives me this warning:
```
/dev/dm inode doesn't exists.
Partimage can create it for you.
You can also use the manual mknod
command. Do you want this inode
to be created for you now?
```

I said yes, then it shows me the partitions.
Direct copy of PartImage screen:
```

     &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Partition Image 0.6.4 &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474; * Partition to save/restore                                       &#9474;
     &#9474;   sda1                                 ntfs         120.00 GiB  &#8593; &#9474;
     &#9474;   sda2                                 -unknown-    91.27 GiB   &#9646; &#9474;
     &#9474;   sda3                                 -extended-               &#9618; &#9474;
     &#9474;                                                                 &#9618; &#9474;
     &#9474;                                                                 &#9618; &#9474;
     &#9474;                                                                 &#9618; &#9474;
     &#9474;                                                                 &#8595; &#9474;
     &#9474;                                                                   &#9474;
     &#9474; * Image file to create/use                                        &#9474;
     &#9474;   ______________________________________________________________  &#9474;
     &#9474;                                                                   &#9474;
     &#9474; Action to be done:                                <Next (F5)>     &#9474;
     &#9474; (*) Save partition into a new image file                          &#9474;
     &#9474; ( ) Restore partition from an image file          <About>         &#9474;
     &#9474; ( ) Restore an MBR from the imagefile                             &#9474;
     &#9474;                                                   <Exit (F6)>     &#9474;
     &#9474; [ ] Connect to server                                             &#9474;
     &#9474;     IP/name of the server: _________________________ Port: 4025__ &#9474;
     &#9474;     [X] Encrypt data on the network with SSL                      &#9474;
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


```

Like i said, I don't think it's giving me an accurate readout of my partitions. First of all, it's showing that they're a part of sda, which is the physical HDD, not the logical RAID volume. Secondly, it says the second partition is of unknown format, when it should detect it as being ext3.

So, what can I do? I would like to backup my Linux partition every so often to a partition on the disk. Maybe use the free space available as a backup partition. But that makes me nervous, because the last time I used GParted to create a new partition out of nothing, it promptly corrupted the partition table somehow. Maybe it was user error; I dunno. Anyway, how can I get PartImage to read my drives correctly? 

Thanks!

Also, on a side note: how big should my Linux partition really be? I set it at 90GB just to give me a good solid number, but I've worked on some Linux machines and have never really seen it go over 30GB used. I'm not using it for gaming or anything like that (that's where Windows come in at), just general web browsing, everyday stuff, eye candy... >_>

---

