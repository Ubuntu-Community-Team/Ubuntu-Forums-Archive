---
title: "Registry in Linux"
date: 2008-12-24
forum: General Help
---

### Post by alan_uk on 2008-12-24
Firstly, when I had XP I used to use registry cleaner to clear up any unwanted remnants and faults. Is there a counterpart in Linux? and secondly do you need to defrag the hard drive?

---

### Post by ajcham on 2008-12-24
Short answer: no and no.

Longer answer:

Linux doesn't use a registry for program configuration.  For the most part each program stores it's own config in a file or subdirectory in /etc.  Unlike the Windows registry, performance won't be hindered by having excess remnants in here, [s]but I believe an 'apt-get autoclean' will remove superfluous config files (although I may be wrong on that).[/s]*

The filesystem used by Linux works differently from that in Windows so defragging is not necessary. Put simply it uses the disk in such a way as to minimise fragmenting in the first place, by only writing to areas with enough space, and by reorganising on the fly. Futher info can be found here: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

EDIT:
* Turns out I was (very) wrong - however, excess config files can be removed in Synaptic by selecting 'Status', then 'Not Installed (residual config)'.

---

### Post by bodhi.zazen on 2008-12-24
See these links :

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html) 
    [http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles) 
    [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920) 
    [http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

---

### Post by Grout58 on 2008-12-24
To answer your questions 

1: The file systems ext2/3 which is what your most likely using on ubuntu does not need to be defragmented.

2:  Ubuntu does not have a registry, it used config files usually found in /etc/ There is no need to do anything to these files unlike windows.

Hope that helps.

Have a good holiday.

---

### Post by alan_uk on 2008-12-25
Many thanks for the information

---

### Post by iponeverything on 2008-12-25
There has been some controversy regarding this, in the past the windows registry has often been regarded as a weak link at best and at worst, a major design flaw.  When gnome adopted a similar system, there was a fairly heated debate going on.. 

```
sudo apt-get install gconf-editor
```

then run:

```
sudo gconf-editor
```

to edit the gnome registry. When you get into it you see that it does resemble the windows registry.

---

### Post by Andrew.Z on 2008-12-30
> **alan_uk said:**
> Firstly, when I had XP I used to use registry cleaner to clear up any unwanted remnants and faults. Is there a counterpart in Linux? and secondly do you need to defrag the hard drive?

[BleachBit is a file cleaner Linux](http://bleachbit.sourceforge.net). It supports many applications, system files, and even "registry" entries,

> **Grout58 said:**
> 2:  Ubuntu does not have a registry, it used config files usually found in /etc/ There is no need to do anything to these files unlike windows.

It's not accessed consistently by a single API like Windows or stored the same way, but [Linux does have a registry which can use cleaning](http://bleachbit.sourceforge.net) sometimes.  Linux's "registry" is an array of standards (de-facto, proposals, policies, etc) stored in files in various locations.

---

### Post by dcstar on 2008-12-30
> **iponeverything said:**
> There has been some controversy regarding this, in the past the windows registry has often been regarded as a weak link at best and at worst, a major design flaw.  When gnome adopted a similar system, there was a fairly heated debate going on.. 
........
to edit the gnome registry. When you get into it you see that it does resemble the windows registry.

Apples<>Oranges. The Windows Registry contains data about every single part of the system, the Gnome configuration database contains configuration information about the Gnome DESKTOP.

Linux systems do not have to use the Gnome Desktop, and it only affects that small subset of a Linux system.

Lose you Gnome configuration and you might have a strange looking desktop that is easy to set back to defaults, lose your Windows Registry and you system is hosed.

---

### Post by Andrew.Z on 2009-01-06
> **dcstar said:**
> Apples<>Oranges.

Who said anything about the Gnome configuration database?  I'm talking about all the Linux registries
* /etc/xdg/autostart/
* /usr/share/applications/
* /usr/share/mimelink/
* the user-specific counterparts of the above
* Gconf ("GNOME configuration database")
* RPM or DEB database
* and a dozen other places used to "register" applications, shortcuts, file associations, context menus, etc.

> Linux systems do not have to use the Gnome Desktop

Many Windows apps don't use the Windows registry at all.

> Lose you Gnome configuration and you might have a strange looking desktop that is easy to set back to defaults, lose your Windows Registry and you system is hosed.

Sorry, *this* is apples to oranges.  In Windows, it's "safe" to delete the HKCU (current user) registry like it is safe to delete the local gconf registry (either resets user-specific settings).  However, neither on GNOME or Windows is it safe to delete the system registry.  If you don't believe me, delete /etc/gconf/, or if we are being more broad about the term "registry," then also delete all the directories at the beginning of this post.  Do that and Linux is hosed.

---

