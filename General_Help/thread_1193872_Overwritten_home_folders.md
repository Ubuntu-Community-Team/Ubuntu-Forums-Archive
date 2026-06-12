---
title: "Overwritten /home/ folders"
date: 2009-06-22
forum: General Help
---

### Post by chifeatures on 2009-06-22
Hi there, my partitions have been seriously playing up and I've been fixing many orphaned blocks and inodes over the past few weeks using fsck. I replaced my hard drive with a brand new on and it's continued to do it - I assume my computer has a faulty controller or something as it was a fresh Ubuntu 9.04 install with very little tweaking.

Last night I turned on my machine and nautilus threw up an error when I got to the Desktop saying "/home/***/Desktop could not be produced" with no files being displayed on the desktop either. After having a look at my /home/***/ folder in terminal, I saw a few folders which looked like:

 ??????? ?????????? Documents

When I tried to open them or chmod/chown I got the error: "stale NFS file handle". These folders have nothing to do with NFS as far as I know, they are just standard /home/***/ folders on a partition.

As well as this, some folders are now files! The folders: Desktop,Music,Pictures,Public (so this is the reason I'm writing this, I've lost a massive amount of data). A stat of one of these folders reads:

File: `Music'
Size: 11274     Blocks: 24     IO Block: 4096     regular file
Device: 804h/2052d     Inode: 9707533     Links: 2


So my question is, is there a way to "see" the data underneath these folders? The df -h reads that i'm still using all the data I was before so if only I could turn these files into folders again that would be awesome. Many thanks for getting this far down and any help would be massively appreciated! =)

Some info:
Ubuntu 9.04 x86_64
Dell XPS M1330
FS: ext3
Been using Ubuntu for over 2 years
Been using Linux for over 4 years

---

