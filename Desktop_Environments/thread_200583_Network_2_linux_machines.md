---
title: "Network 2 linux machines"
date: 2006-06-20
forum: Desktop Environments
---

### Post by bazzer on 2006-06-20
Hi all

I'm still a pretty green noob, but I am taking the bull well andt truly by the horns here... Let me explain my setup. 

First off, I've got a wireless broadband router job, which it cool. Next, I've got 2 PCs in my home, one downstairs by the telly, it's a 1GHz Compaq Evo SFF desktop, and I've prettied it with a TFT and mini keyboard (as well as a COOL custom mousemat platform for my armchair... but that's a whole new story). It's got Suse 10.0 on it and I use it for hosting a development website and for surfing purposes. I also want to do some moderate web design on it, within the 'confines' of Linux. Don't want to install loads of gumph to accomplish a task I could do under Windows in a few mins etc...

My main PC is upstairs, it's a quicker 2.6GHz scratchbuilt thing, works great with a fresh install of XP, dual booted with Ubuntu 6.06. I can share my MP3s with Windows, cos they're on a FAT32 partition, and I can at least read my NTFS partition to get at my My Documents folder. It connects to the router via the wireless no probs thanks to a how to on here... (cheers again guys!)

Now, the beef: I know how to share a windows folder so I can get it from my Suse box, no probs at all. But how do I share a partition from Ubuntu to Suse?? The partition is mounted as 'MP3' on my desktop, and I've looked into the properties and permissions of the folder but I can't change any permissions because it's a partition!!

Little help please?

---

### Post by ayoli on 2006-06-20
go to menu Administration > Shared Folders , then clic the add button select your folder/disk you want to share.
hope that helps.
cheers.

---

### Post by bazzer on 2006-06-20
ok done that - but how do I access the share from Suse - after all, I haven't added any permissions etc.... I have added a new user on the Ubuntu box, but I xcan't see where I can assign permissions to the share. See what I mean?

BTW, I can see the share is there from the Suse box, just get 'access denied' when i try to list what's inside...

---

### Post by ayoli on 2006-06-20
depen of samba security level if it's share then allthe allowed host should browse your share, if it's user then the user of the outbox must exist on your ubuntu box.
once you have your user added on your box, to set samba password type in a terminal:
```
sudo pdbedit -a -u user_name
```
then try again to connect to your share from your suse box (in nautilus: computer > network), and enter the username and password when asked.

---

### Post by yopnono on 2006-06-20
Add a user  like nornal or use a user you have then use this to add the user to samba shared folder.

```
sudo smbpasswd -a "username of user you like to add"
```

---

### Post by bazzer on 2006-06-20
cracking did that thanks guys!

---

