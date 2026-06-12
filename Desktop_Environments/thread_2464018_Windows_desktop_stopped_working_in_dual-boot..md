---
title: "Windows desktop stopped working in dual-boot."
date: 2021-06-23
forum: Desktop Environments
---

### Post by davidjj2 on 2021-06-23
I have been redirected here from HP Forums. I installed a Windows 10/Ubuntu 20.04 dual boot, on a new HP 17ca1500 laptop. It worked well for a month, but then last week, the Windows desktop "died". The GRUB boot still works, and so does the Windows login screen; but when I reach the normal Windows desktop picture, there is nothing on it -no apps, no control panel, no file manager, just the Windows start button, which does not work. Ubuntu is still working perfectly, and I can see the Windows files in "Other Locations", but I can't open any of them as their format is not compatible with Ubuntu.  The Windows partition shows as "unmounted" on the Disks app. Could anyone guess what is going on, and what I can do about it?

---

### Post by yancek on 2021-06-23
From your description I would say this is a strictly windows problem.  Once you select windows from the Grub boot menu, Ubuntu and Grub are no longer involved as selecting windows turns the system over to the windows bootloader.  HP probably referred you here because you told them you had Linux/Ubuntu installed so they could pass the problem on to someone else.  They don't (like other manufacturers) offer support for anything but the installed system when purchased, in your case windows 10.

Could you describe in more detail what "died" means in reference to your OS?  What exactly happened?  Did you make any changes to the windows OS the last time you were booted to it?  If so, what changes?

You should be able to access windows filesystems as ntfs-3g (needed to access windows ntfs filesystems) should be installed by default.  Linux permissiions/ownership are not understood by windows systems so you need to use umask, dmask, fmask.  That's a separate problem and you should only access ntfs data partitions and not the OS (C:\ drive) system files from Linux.

Your problem is windows, so either try calling HP again and don't mention you have Ubuntu/Linux installed because it is irrelevant per your post.  Otherwise, try a windows 10 forum or give more information by answering the questions  I posted in paragraph 2 above.

---

### Post by davidjj2 on 2021-06-23
Re. your 2nd paragraph: The last time I went into Windows 10, everything was perfectly normal. (There* may* have been a Windows update, but I would not swear to that.) The next time I went in, I got my usual desktop picture, but all the apps and everything else had vanished except the Start button, which did not work.
I wonder if you could explain how to use the ntfs 3g system, as I am stlll fairly new to all this.
Thanks. David J.

---

### Post by oldfred on 2021-06-23
Can you directly boot Windows from HP's UEFI boot menu? Most HP:
HP - escape + F9 for boot menu, F10 for bios setup

Windows updates often turn fast start up back on which sets hibernation flag.
Grub will only boot working Windows, or Windows that is not hibernated. But then you should still be able to directly boot from UEFI menu.
or from direct boot of Windows & f8 to get into its own repair console.
Or you may need to use your Windows repair/recovery drive, which of course you made, along with good backups of all installed systems as soon as you installed & then regularly updated.

---

### Post by yancek on 2021-06-23
You need to mount it or create an entry in the /etc/fstab file to have it mount permanently with the permissions you want.   For this you would use the umask, dmask and fmask options to get the options you want.  You should be able to get info on that by searching these forums or doing an online search to find how to get the permissions you want which we don't know. 

Trying to repair your windows from Ubuntu or any Linux by modifying windows system files is not a good idea.  Do you have a recovery CD/USB as suggested above for windows?  Better option.

Also, if you can boot windows from Grub and get to the windows login screen and login, I doubt it is a problem with Grub.  I'd again suggest going to a windows forum with your problem and there is no need to mention you are using Ubuntu.i

---

