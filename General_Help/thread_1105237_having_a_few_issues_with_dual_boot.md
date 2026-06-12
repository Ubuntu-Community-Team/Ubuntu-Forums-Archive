---
title: "having a few issues with dual boot"
date: 2009-03-24
forum: General Help
---

### Post by Los Frijoles on 2009-03-24
I am dual booting XP home and ubuntu 8.10 on my Acer Aspire One. I usually use Ubuntu since after installing MS Office on it I have had no real reason to go back very much except to play games (Zelda on project64, etc) or write up documents (Word has a few issues with wine).

Anyway, I have been doing a few things I am not sure are the best practices and I also have noticed a few problems:
- I have mounted my My Documents folder on the windows partition into the Documents folder so that I can share documents between the two OSes. Is this a bad idea? I had to recover a few windows system files after 2 months of not using windows. Would this cause that?
- My wireless card doesn't move off of "getting ip address" in windows. This started after I installed ubuntu, but I am not sure why that would affect it. The card is an Atheros AR5BXB63

---

### Post by tripolitan on 2009-03-25
What exactly are these "issues"?

-How did you "mount" My Documents? did you use symbolic link or another method?

-What actually happened that made you "recover" windows system files? did windows crash? were you unable to dual boot?

-Ubuntu installs in a separate partition, it does not interfere with windows, unless you have write permissions AND you intentionally messed with windows system files. Please keep in mind that Windows NTFS uses permissions and it is very possible that these permissions for the system files that you have "recovered" using Ubuntu, have changed.

Boot back into Windows and fix the permissions on everything under the windows directory and all of its sub directories.

Personally, while using Ubuntu, I would not mess with anything outside of C:\Documents and settings\username\My Documents\

Hope this helps

---

### Post by 3Miro on 2009-03-25
I prefer to mount my windows partition to /media/winc and then symlink MyDocuments to WinDocs folder in /home/me.

Nothing that you do in Ubuntu shouldn't affect anything in Windows in general. Unless you copy/paste files between Linux and the system folders in windows then you will not have trouble.

It is probable that the windows issue is just a windows issue. Sometimes newer windows updates would break older hardware drivers and such (I know many people that complain about Bluethoot being broken by windows updates).

---

### Post by mb_webguy on 2009-03-25
IMO, the best way to set up your system for a dual boot is to use a small partition for each OS and its applications, a very small home partition for Ubuntu, and a large shared data partition.  It's generally a bad idea to expose one operating system or its configuration files to another.

Ubuntu can live comfortably on an 8-12GB partition, XP needs about 12-15GB, and I wouldn't put Vista on anything smaller than about 25GB.  

I suggest a small (<2GB) separate home partition for two reasons.  First, you want to keep your Linux configuration files away from Windows, and so you don't want to just mount the shared data partition as your home directory.  Second, it's good to keep your configuration files separate from your OS, because a) it can make things easier if you need to reinstall Ubuntu, and b) it prevents you from accidentally locking up your installation by running out of space, which is easy to do if you keep home on the Linux partition.

The shared partition can be formatted as either ntfs or ext3, depending on your primary OS.  Vista allows you to move the location of your user folders, but in Ubuntu and XP you'd have to replace them with shortcuts/symlinks to folders on the shared data partition.

---

### Post by tripolitan on 2009-03-26
> The shared partition can be formatted as either ntfs or ext3, depending on your primary OS.

To the best of my knowledge, ext3 file system cannot be written to from Windows, NTFS read write support in Linux, although exists, is not quite 100%. FAT32 is more easily accessible and does not care about permissions.

By the way, has anyone narrowed down the exact problem of the original poster?

---

