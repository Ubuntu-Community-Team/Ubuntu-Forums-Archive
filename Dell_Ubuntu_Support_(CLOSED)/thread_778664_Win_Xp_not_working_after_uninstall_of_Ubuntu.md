---
title: "Win Xp not working after uninstall of Ubuntu"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by krama09 on 2008-05-02
Hello I am completely new to linux.
I have downloaded Ububtu 8.04 LTS and installed in My Dell Inspiron 6000 laptop inside Windows XP Media Center Edn 2005(using Wubi).
It was working fine. Once accedentally power went off while working in Ubuntu and after restarting I could work in XP with out any problem.

However, when I restarted Ubuntu...it did not boot in normal way and only command prompt appeared (Debian....version)...I tried some commands mentioned in help...but of no avail.Later on I started XP and uninstalled ubuntu.

Subsequently, When I restared in XP...chkdsk started saying volume(ntfs) is dirty and later on automatically took several actions..one of them is "changing corrupt security id to default security id of file___". Afterwards XP started. But none of the XP related applications (including word,ie)are not working throwing some exceptions. Even taskbar, start menu disappeared. Only non microsoft applications like acrobat, Firefox, are working.

I could not run XP properly neither could restore...

Several posts mentioned that installation inside Win XP will not modify hard disk partitions...But it appears it is not true...at least in my case it corrupted NTFS partition...

Can anyone help to restore XP on my Dell Laptop?

---

### Post by phndrummer on 2009-02-21
did you try and boot xp in safe mode? I think it's F8 or F10 when you see the dell logo

---

### Post by Rallg on 2009-02-22
I searched a bit. I located a particular complaint involving virtualization software (which could be the issue here), and other problems unrelated to Linux or virtualization.

It seems that Windows chkdsk sometimes finds problems, then "fixes" them in  a way that messes up the file system. It is rare, but it happens. It seems to be a Windows problem, not a Linux problem (although using the virtualization might have triggered the problem). Within the virtualization, were you using any very large files (more than 2Gb, such as a movie)? One complaint suggested that the problem was caused by large data files (unverified).

Nobody offered a good solution.

Can you make a backup copy (to external media) of all your personal files? Do it. If you cannot get access to your files from within Windows, you can probably do it using live Linux, launced from a USB drive or CD-ROM, then copy your files to a USB drive for safekeeping.

It is possible that you might have to reinstall Windows. If your machine did not come with XP installation media, then it probably has an "I386" folder somewhere, with the essential installation files. It is possible to reconstruct a Windows re-installer from those, using a trick known as "Bart PE" (search for it).

If your problem could be traced to one or two system files, they could be replaced (this is not easy in Windows). But the other complaints suggest that there is likely to be widespread damage.

---

### Post by dark_religion on 2009-11-13
When i had this I had to reinstall windows.

---

### Post by MichealH on 2009-11-13
... or you can change your /boot/grub/menu.lst file to add it to the list maybe that is a bit out.

---

