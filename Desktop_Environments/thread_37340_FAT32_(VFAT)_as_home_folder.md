---
title: "FAT32 (VFAT) as home folder?"
date: 2005-05-26
forum: Desktop Environments
---

### Post by royg1234 on 2005-05-26
What do you guys think about using a FAT32 or VFAT (what's the difference?) as a home folder?  Bad idea?

---

### Post by dave9191 on 2005-05-26
I was going to do this, but something came up which meant that it was a bad idea. I cant remember exacly what, but I think it was a number of files that work fine on ext3, didnt want to copy over to fat32. And I didnt want to end up not being able to save files. 

Dave

---

### Post by Sleeper Service on 2005-05-26
Bad idea.  Fat32 isn't a proper multi-user filesystem and you don't get the full permissions options you get with ext2/3.  As far as I know, all your /home/user directories would be readable/writable/executable for anybody else.

If it's to have easier cross communication on a dual-boot Win/Ubuntu machine, I'd suggest having a Fat32 D:\ partition for your data in Windows, mounting this in Ubuntu as /mnt/win_d/ and then perhaps even creating a symbolic link from your  home directory.

Hope that makes some sense :)

---

### Post by stoneguy on 2005-05-26
So bad an idea that it might not even be possible. Anything that tries to chmod or chown anything put into ~/home (highly likely when software is installed) is probably going to bomb.

---

### Post by royg1234 on 2005-05-27
lol.  Thanks.  Yes, dual-booting is what it's for, with the FAT32 drive for music, so it wasn't that big of a deal.  I'm just under the impression that browsing through it's a little bit slower than the ext3 partition because it's mounted.

And how do I make a "symbolic link"?  I haven't been able to figure out how to make shortcuts like in Windows (right-click drag > "create shortcut here").

Could I just mount the VFAT straight into my home folder?  or bad idea too?

---

### Post by Sleeper Service on 2005-05-27
[QUOTE=royg1234]And how do I make a "symbolic link"?[/QUOTE]
I'm assuming you've got a Fat32 partition which you've already mounted to /mnt/win_d, and you'd like a link to this from your /home/royg1234/ (or whatever!) directory.

1. Open a terminal (on opening you should be in your user directory).
2. type [FONT=Courier New]ln -s /mnt/win_d/ win_d[/FONT]
3. That's it!

It will now appear like you've got a directory /home/royg1234/win_d which contains everything on your Fat32 partition.

Links in Linux are much more subtle that "shortcuts" in Windows.  They don't just help you skip to another location - they actually become alternative file paths.

---

### Post by stoneguy on 2005-05-27
I read the original questionner to mean he wanted the entire home directory on FAT32.

I saw (somewhere) a trick for sharing a single set of Thunderbird mail files under dual boot by installing the Win version first, then linking the Linux directory to the Win one. That's a very useful instance of what you suggested.

---

### Post by royg1234 on 2005-06-03
> 1. Open a terminal (on opening you should be in your user directory).
2. type ln -s /mnt/win_d/ win_d
3. That's it! 
How do I make it do this automatically on startup?

or what if I just set the FAT drive's mount directly in my home folder.  (good so that beagle can search it).  Is this bad too?

---

### Post by royg1234 on 2005-06-03
or what if I just set the FAT drive's mount directly in my home folder.  (good so that beagle can search it).  Is this bad too?

---

### Post by dave9191 on 2005-06-03
you can edit your fstab file in the /etc folder to have it mount automatically on boot. And mounting it in your home dir should be fine :)

Dave

---

