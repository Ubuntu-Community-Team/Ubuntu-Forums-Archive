---
title: "Minimum needed for hibernate and suspend"
date: 2009-05-30
forum: General Help
---

### Post by keithpeter on 2009-05-30
Hello all

I've installed stock Ubuntu 9.04 onto an old laptop. Hibernate and suspend are working fine when I set the appropriate settings in the gnome power manager.

I'd like to use much lighter software on this 256Mb ram laptop (standing memory use is 90 to 100 Mb and I'm going into swap when running any applications).

What is the minimum I need to get hibernate on close lid and suspend working? How do I find out what packages are needed over a cli install? Do I need gdm and the gnome power management stuff?

Thanks

---

### Post by ugm6hr on 2009-05-30
For suspend to RAM, 1.5x RAM is recommended for swap.  Hibernation should work with anything, since it hibernates to your HD (not RAM / swap).

No packages are needed over a cli install; it will work just fine (as a cli linux distro).

If you want a stripped-down Gnome, then see [http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)
It is designed for Intrepid, but should apply to Jaunty too.

If you actually want something lighter, try LXDE: [http://ubuntu-lxde.wikidot.com/](http://ubuntu-lxde.wikidot.com/)

Or XFCE (*sudo apt-get install xfce4)*

---

### Post by keithpeter on 2009-05-30
> **ugm6hr said:**
> No packages are needed over a cli install; it will work just fine (as a cli linux distro).

Thanks for this reply, reassuring. Is there anything I have to do to 'enable' hibernation on a bare CLI install? 

The stock Ubuntu with the full Gnome desktop has hibernate switched off in the power settings. I'm therefore assuming that I have to tell a CLI installation to catch the lid closing event and to hibernate.

LXDE is great, and I'm quite into dwm as well.

---

### Post by kerry_s on 2009-05-30
```
sudo apt-get install pm-utils uswsusp acpi-support
```

---

### Post by keithpeter on 2009-05-30
> **kerry_s said:**
> ```
sudo apt-get install pm-utils uswsusp acpi-support
```

Thanks once again kerry_s. I'll read the man pages once I do a clean CLI install so I know how to enable hibernation.:p

---

### Post by keithpeter on 2009-05-30
Hello All

CLI install from the netinstall cd image for 9.04 Jaunty, then, as suggested by kerri_s

```
sudo aptitude install pm-utils uswsusp acpi-support
```

and I can hibernate and resume using

```
sudo /etc/acpi/hibernate.sh
```

Resume gives lots of errors about fans not found &c. This works both at CLI and in a terminal under dwm.

The thread at

[http://ubuntuforums.org/showthread.php?t=813387](http://ubuntuforums.org/showthread.php?t=813387)

made me aware of a package called powermanagement-interface. Installing that means I can issue a command in a terminal
(not sudo) under dwm thus 'pmi action hibernate' and the laptop does and then resumes without any errors.

Same command at the CLI prompt before startx results in errors like

```
Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy...
```

Now: how on earth do I 'catch' the laptop lid closing event and use that to issue the 'pmi action hibernate' command? Any pointers welcome.

---

### Post by niteshifter on 2009-05-30
> **ugm6hr said:**
> For suspend to RAM, 1.5x RAM is recommended for swap.  Hibernation should work with anything, since it hibernates to your HD (not RAM / swap).

Eh what? I believe that you have that backwards: Suspend (CPU to idle, RAM remains powered up so that contents are preserved, ACPI state S3) requires nothing from the HD. Hibernate needs someplace to write RAM to, either a dedicated swap partition or a swap file as the machine is fully powered down in this state (ACPI state S4).

---

### Post by kerry_s on 2009-05-30
> **keithpeter said:**
> Hello All

CLI install from the netinstall cd image for 9.04 Jaunty, then, as suggested by kerri_s

```
sudo aptitude install pm-utils uswsusp acpi-support
```

and I can hibernate and resume using

```
sudo /etc/acpi/hibernate.sh
```

Resume gives lots of errors about fans not found &c. This works both at CLI and in a terminal under dwm.

The thread at

[http://ubuntuforums.org/showthread.php?t=813387](http://ubuntuforums.org/showthread.php?t=813387)

made me aware of a package called powermanagement-interface. Installing that means I can issue a command in a terminal
(not sudo) under dwm thus 'pmi action hibernate' and the laptop does and then resumes without any errors.

Same command at the CLI prompt before startx results in errors like

```
Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy...
```

Now: how on earth do I 'catch' the laptop lid closing event and use that to issue the 'pmi action hibernate' command? Any pointers welcome.

the acpi thing, in /etc/default/acpid uncomment:
**MODULES="all"**

the hal thing, stupid policykit requires a login manager or it can't tell you logged in. the work around i use is to add a line in **/etc/PolicyKit/PolicyKit.conf** the line is "**<return result="yes"/>**" what it does it tell it yes to everything,after that you should have no more hal/policykit problems. here's what mine looks like, i still do it even though i don't have problems, it's a "just in case".

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
  <return result="yes"/>
</config>


```

---

