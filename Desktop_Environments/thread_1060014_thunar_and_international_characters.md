---
title: "thunar and international characters"
date: 2009-02-04
forum: Desktop Environments
---

### Post by Hooya on 2009-02-04
I installed xubuntu on my laptop, it has several sets of libraries from gnome and kde and I run Fluxbox as my window manager.  I have three partitions: / /home and swap.  All were created using the installation wizard.

Folders and files in my /home directory that should contain special characters such as umlauts, accents, and other international characters do not show correctly in Thunar.  They show as a black diamond with a ? inside it.  I know that Thunar can show these files correctly, as my desktop, also running Fluxbox with Thunar for the file manager, displays these characters correctly (even on ntfs mounted drives)

/etc/fstab for both of these computers does not specify a locale (utf-8 or similar) for any of the hard drives, so I do not believe that is the difference.  I think it must be in something that I have installed on my desktop (which has complete ubuntu-desktop and kubuntu-desktop packages installed) that allows Thunar to correctly display the international characters and I am missing that package on my laptop.

In case it is fstab, here is the contents of my fstab file for my laptop:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=51afa182-aeb2-4514-992c-4cdca337e69e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=f4a06eb6-11e6-4499-9bcd-c362e53ea5cb /home           ext3    relatime        0       2
# /dev/sda1
UUID=8df24ccd-b037-435d-9734-76f54d243265 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I'm up for tweaking, I just don't know what to tweak.  I think it's just a package I'm missing, but I've compared installed packages between my desktop and laptop using the same search patterns and haven't figured out what is missing.

---

### Post by Hooya on 2009-02-04
I hate to bump, but this is going to get totally ignored.  Someone here has got to know the solution to this.

---

### Post by BluntedBoyWonder on 2009-02-16
I have got the same problem as this user.

I have a dual boot set up - windows xp / xubuntu. Both OSs access an external hd (NTFS) I have set up with a lot of mp3s. Many of these mp3s have accents in the titles. These files and folders remain ***invisible*** in Thunar and Exaile (my media player of choice)

 So it's not just a matter of misprinted symbols for me- xubuntu cannot even *display* entire folders on my machine.

---

