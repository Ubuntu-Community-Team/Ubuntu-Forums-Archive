---
title: "General NTFS question - good, no good?"
date: 2009-01-25
forum: General Help
---

### Post by tullmejs on 2009-01-25
Hello, I've got a xubuntu 8.10 installation and as I connect an external usb hard drive, ntfs, I sometimes experience problems.

Without expanding on that, is it _generally unwise_ to use ntfs with (x)ubuntu if one does not have to? 

I have a lot of data on the drive, so reformatting would be awkward, and I might actually want to revert back to Windows soon, who knows. But if ubuntu and ntfs is not going to get along very well it may well be worth it all the same. I do not dual boot, of course.

Please advise!

---

### Post by xc1024 on 2009-01-25
ntfs is not a very good thing. don't use it if you don't have to. 
it works well for me, but i'm using it on only one partioton.

---

### Post by drs305 on 2009-01-25
*Unwise* wouldn't be the word I would use, but I'd ask myself this: If I was going to only eat pasta for the rest of my life, would I stick to a spoon or would I change to a fork? ;-)

Seriously, ntfs is a non-native file system to linux. It can work but not nearly as well as ext3. It doesn't support the linux permission structure and mounting/unmounting can be problematic. 'Unclean' shutdowns are a regular topic on the forums.

On the other hand, *if* you really think you might go back to windows and the process is going to be tedious to you, you can continue to use ntfs if you desire. The utilities "*ntfsprogs*" can help with things like labeling and ntfs-3g has come a long way in making this format more usable in linux. If you explain the problems you are having we can probably find solutions.

You don't seem quite ready to jump fully into ubuntu, although I highly recommend it. The only reason to stick with ntfs is if there is a good possibility you will be returning to windows - even then there are apps like ext2fs that can read ext2/3 from windows.

So come on, grab that fork!

---

### Post by tullmejs on 2009-01-25
Thank you. My problems may originate in hardware, as I have some other problems that are definitely non OS-ish.

But I don't need potential errors. I'd rather endure the process of changing file systems, I think. Forks for pasta!

---

### Post by tullmejs on 2009-01-25
I formatted the drive to ext3 and configured it to automount, and it actually did :-)

Then, alas, fsck said things I will not utter here. I hope those hardware issues are to blame. I'll see to that before revisiting my software challanges.

---

