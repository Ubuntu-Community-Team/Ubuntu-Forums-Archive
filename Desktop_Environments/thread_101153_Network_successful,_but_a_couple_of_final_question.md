---
title: "Network successful, but a couple of final questions!"
date: 2005-12-09
forum: Desktop Environments
---

### Post by stig on 2005-12-09
Great excitement - but a couple of remaining questions! After months of dabbling with Ubuntu and failing to get my PCs networked, Nautilus-Share has solved almost everything. I have a couple of related problems which - if solved - would give me a 100% network.

I previously tried all the HOWTOs and guides, using NFS and Samba, but could never get a proper functioning network. I am a Linux newbie and I don&#8217;t know much about computers but I have had a network of several PCs in Windows for many years. Ubuntu breezy seems great but the biggest problem for me, as someone working from home with a small business, was that I couldn&#8217;t get the network figured.

Then I recently saw Nautilus-Share mentioned a couple of times in the Ubuntu Forums. It was very easy to download and instal. Within an hour I had my three PCs networked successfully. I have one Ubuntu PC, one Win98 PC and one with two hard disks - Ubuntu and Win98.

Now I can see shared folders from Ubuntu to Ubuntu, Windows to Windows, Ubuntu to Windows and Windows to Ubuntu. At last - marvellous!

But now the remaining problems! On the PC with two hard disks, I can&#8217;t see the shared folders on the Win98 disk from the Ubuntu disk and vice versa when I look at the network. Is this done some other way rather than by networking?

Also, when the dual disk PC is in Win98, the other two PCs can see the Windows shared folders but they cannot see the ones on the Ubuntu disk. Not knowing much about computers, I&#8217;m not sure - should it be possible or not?

Finally, I explained above that in most cases I can see the shared folders across the network and open and view files in those folders. Between Windows computers I can move files between the shared folders. But how do I move them between Ubuntu computers and between Ubuntu and Windows? If I try to paste a copied file into a shared folder belonging to another PC I get:
Error &#8220;Access denied&#8221; while copying &#8220;/home/username....filename&#8221;

Does this mean permissions need changing somewhere? It applies whether I am trying to paste into a Windows or an Ubuntu shared folder.

Sorry about several questions at once, but they are related to the same overall problem!

---

### Post by tomski on 2005-12-09
this is not due to networking it's because when win 98 is running it cannot read linux partitions, but if you are using fat file system in win 98 you should be able to have linux mount that drive during boot up (assuming you have win98 & ubuntu installed on the same pc) by editing a file called fstab which lives in /etc/fstab

once you have ubuntu mount that disk you can then share it like a normal linux share

and yes your final problem may be that the user trying to copy the files is not a valid user on the recieving pc ie you need to have the same user name on the machine you are trying to write to

---

### Post by stig on 2005-12-09
[QUOTE=tomski]this is not due to networking it's because when win 98 is running it cannot read linux partitions, but if you are using fat file system in win 98 you should be able to have linux mount that drive during boot up (assuming you have win98 & ubuntu installed on the same pc) by editing a file called fstab which lives in /etc/fstab

once you have ubuntu mount that disk you can then share it like a normal linux share

and yes your final problem may be that the user trying to copy the files is not a valid user on the recieving pc ie you need to have the same user name on the machine you are trying to write to[/QUOTE]

Thanks for the help! Looking at the Ubuntu Unoffical guide it suggests I edit /etc/fstab/ as follows to "mount Windows partitions (FAT) on boot-up, and allow all users to read/write": 
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

If I do this, do I first need firestarter on the linux disk to prevent anyone getting at my Windows files through the mount? Or is this a silly question?

On your final comment about valid users, do you mean I have to create Fred as a second user account on Bill's computer and Bill as a second user account on Fred's? Or is it a case of changing permissions on folders? In either case, I don't know what I would do with the Windows 98 PCs because I don't have users or passwords on them.

---

