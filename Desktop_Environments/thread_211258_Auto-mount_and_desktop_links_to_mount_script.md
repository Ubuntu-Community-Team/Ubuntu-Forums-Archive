---
title: "Auto-mount and desktop links to mount script"
date: 2006-07-08
forum: Desktop Environments
---

### Post by inspired on 2006-07-08
Hi there,
I would like some advice on the best way to go about implementing the following. I am sure it's a common want from win/linux users, and I have found various tips on how to do some of this, but nothing that seems to work in the way I would like. So I am asking for help directly.

The computer has three HDDs. One is set up purely for Ubuntu.
The other two are all NTFS and were there for the existing winxp system.
I have two users set up on Ubuntu. I would like each user to have an easy, simple way to access their My Documents data on the NTFS partitions. For one of these users the data is stored in an entire partition called "Working files". For the other user it is stored in the default ../My Documents folder in that users profile AND in a folder in the root of the "working files" partition.

1) I want to be able to have read/write access to the NTFS partitions. I have installed Captive prior to the recent update I did from Breezy to Dapper. I see that Fuse is also installed. I am able to read/write to NTFS via captive.

2) I know how to manually mount an entire partition into linux. Can I mount a folder within a partition?

3) How do I auto mount a partition and give access to both users?

4) How do I set Ubuntu up so that each user will have their NFTS data mounted and then have easy access to it? (such as via a link or icon on the desktop rather than the user haveing to browse through to /mnt/ntfs-working_files or whatever it might be?

5) Is there a nice graphical interface for managing mounts on a per user basis?

6) How do I write/implement a script file that I can execute on the desktop to manually mount/unmount an NTFS hdd?



I've tried playing with autofs but found the instructions I got were not specific enough (they assumed I knew how to do stuff that I knew nothing about).
I use to have an icon for each NTFS mount drive appearing on my desktop. These have vanished. I think this may have happened after the Dapper upgrade.

I am sure more info will need to be furnished by me. Please ask what you need to.
I am also sure there are pages on the net the explain how to do these things... so please feel free to refer me to those pages.

With thanks,


Jonathan

---

### Post by fopetesl on 2006-07-11
I guess, at this stage, I will not be much help.  At least it will bump your post;) 
I am trying to do something similar but not with NTFS just a humble floppy drive mounted automagically.  Mandriva uses [COLOR="Blue"]supermount[/COLOR] but I read some bad press about it so am attempting autofs (or autofs4).
I have been through the following checks:
(a) Can I load and see a kernel autofs module?```
# modprobe autofs
# lsmod | grep auto
autofs   18436  0
#
```so I have a current autofs kernel module which, on my system, is at:
/lib/modules/uname -r/kernel/fs/autofs/autofs.ko
also:
/lib/modules/uname -r/kernel/fs/autofs4/autofs4.ko
("uname -r" is of course my current running kernel which is 2.6.17...)

However, I am at a loss, having searched for a day, as to how to get autofs loaded at boot time.  I know that there should be a script in /etc/init.d/ which tells the loader how to use autofs _and_ there should be several /etc/auto.* configuration files _and_ I should have symbolic links in /etc/rc?.d/ directories.

I could attempt to install another version of autofs using Synaptic which _may_ generate these missing components but am concerned that in doing so I install an incomaptible version and break my system.

Can someone help as to how to manually set up these missing files/links since none of the HOWTOs I have seen tell me?

When it works I'll come back here:-k

---

