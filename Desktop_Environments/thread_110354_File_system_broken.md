---
title: "File system broken?"
date: 2005-12-30
forum: Desktop Environments
---

### Post by Flyn on 2005-12-30
I rebooted my computer todoay, only to find that I have an unattached inode, whatever that means. I have tried using fsck -b with all the backup superblocks thats mke2fs lists, but each time I am told that the superblocks are damaged, though I can easily browse and view the ext3 partition through Windows.
The command I used to use a backup superblock is "fsck -b 32768 /dev/sdb5".
Is the sytnax correct, and does anyone have any other idea what I can do, cause right now I'm stuck booting WinXP.

Thanks in advance

---

### Post by Zwack on 2005-12-30
Unattached inode means either that a directory entry exists that is not actually linked into a directory.  or that the entry exists in the directory but isn't pointing to a file.  This is bad as it potentially means that a file is missing.

Boot into recovery mode, or from a live CD and type

fsck -a /dev/sdb5

Wait until it finishes and see if it reported that it fixed errors.  If it did then run it again until it doesn't fix anything.

Hopefully that is all it will take.

If it's the former then if you look in lost+found on that directory you should have a file.  You should be able to work out if it's something important or not.

I hope that this helps,
    Z.

---

### Post by Flyn on 2005-12-30
I tried that, and I get the following:
"ubuntu@ubuntu:~$ fsck -a /dev/sdb5
fsck 1.38 (30-Jun-2005)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sdb5
ubuntu@ubuntu:~$"

Any suggestions?

---

### Post by Flyn on 2005-12-30
Repeat to self : "I will not try to fsck the swap partition. I will not try to fsck the swap partition." Sorry about that, the damage was in /dev/sdb1, and for some unknown reason I tried sdb4.

Thanks again for all your help. I doubt there is another Linux community that has this much support from its more knowledgable user to the newbie.

---

### Post by Zwack on 2005-12-30
Given how much I paid for the OS and that the free support forum is provided I don't mind... When I've paid for the OS media I expect support from the vendor...

I also suspect that I am an atypical Ubuntu user...  (ten years as a Unix SA, Running Linux since 1993, Using Unix since 1989)...

What little help I can give on here is payment.

On a related note tunefs is one of the few man pages (on HP at least) to contain a joke...

> You can tune a file system, but you can't tune a fish.

It has been pointed out to me that this is wrong because you can tuna fish.

Z.

---

