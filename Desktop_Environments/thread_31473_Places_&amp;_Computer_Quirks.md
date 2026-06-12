---
title: "Places &amp; Computer Quirks"
date: 2005-05-03
forum: Desktop Environments
---

### Post by rickwood on 2005-05-03
Excuse me if this is the wrong place to ask, but I'm not sure if my particular problem better fits in "Desktop" or "Hardware".  I have a triple boot system that is set up like this:

hda1 -> Windows XP
hda5 -> Mandriva
hda6 -> Ubuntu 5.04
hdb1 -> swap
hdb5 -> vfat data partition

I'm using Ubuntu's Grub as my boot loader, and this seems to work very well.  I've had Ubuntu installed for about a week or so, and really like it (I've always used KDE prior to this, and I'm finding Gnome refreshing).  I have modified my fstab file to make WinXP, Mandriva, and my data partition accessible under Ubuntu.  They are mounted as /WinXP, /Mandrake, and /Data, respectively.

Last night when I booted into Ubuntu, something strange happened.  I noticed three new drive icons on my desktop titled, "WinXP", "Mandrake", and "Data".  Cool!  I also noted that these same drives and labels showed up in the "Places" menu and in under "Computer".  Previously, these drives did not show up in the "Places" menu.  They did, however, show up under "Computer", but had generic labels such as "20 Gig Media", "160 Gig Media", or something similar.

I rebooted the computer several times to see if this behavior was repeatable.  To my suprise, it seems hit and miss.  About half the time, these drives show up under "Places" and on my desktop.  About half the time they don't.  But they always show up under "Computer", although when they are not also under "Places" they have the generic labels in "Computer".  If possible, I would like these drives to always show up under "Places", and be labeled properly in "Computer".  Does anyone know what could cause this erratic behavior, or even better, how I can fix it?

After searching the forums a bit, here are some things I tried without success:

1.  I changed the mount points of these drives from /WinXP, /Mandrake, and /Data to /mnt/WinXP, /mnt/Mandrake, and /mnt/Data.

2.  I unounted the partitions and changed the permissions on the mount points to 777.  I then rebooted.

3.  I tried adding the kernel boot parameter acpi=force.

I should note that I do not have any problems with any of these partitions.  They function very well under Ubuntu in read/write mode (except the WinXP ntfs partition, of course, which is mounted read only).  I also have the data partition shared read/write using Samba without issue.

Has anyone else observed this behavior, and does anyone have other suggestions I can try to resolve this issue?

---

### Post by shakin on 2005-05-03
Weird. If you find a way to reliably reproduce the effect (both when they appear and when they don't) you should file a bug report. You might want to file one anyway just mentioning the problem.

Anyway, you can try going to Places / Connect to Server and choosing Custom Location as server type, then input the path to the mount as the URI, eg. /mnt/WinXP

It works for me and the shortcuts always come back after I reboot.

---

### Post by rickwood on 2005-05-03
Thanks for the tip.  This seems to work fine.  The icons reflect network drives rather than local drives, but at least they consistently show up under "Places".

There doesn't seem to be any logic to when these drives show up automatically and when they don't.  Several times I've simply logged in, immediately restarted the computer, and logged in again.  Sometimes the drives show up, sometimes they don't.  Go figure.

Perhaps I should file a bug report on this.

---

### Post by Totzo on 2005-05-04
Hi,

I'm having a similar problem in that when I boot up none of my drives in /media show up on the desktop or in the "places" menu. if I do "sudo invoke-rc.d dbus-1 restart" they immediately show up and all is fine until I logout and login again (same thing).

I realise this isn't the biggest issue but with gnome 2.8 it never was a problem and I do switch my computer off and on often! Is this a bug with 2.10?

---

### Post by infinito on 2005-05-04
This is a well known bug in HAL, but people ay Ubuntu seem to be busy with other things... I think this is a IMPORTANT bug, and it should be fixed!

You can read the bug thread here:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7641](https://bugzilla.ubuntu.com/show_bug.cgi?id=7641)

---

### Post by rickwood on 2005-05-04
Thanks for the replies.  Looks like a lot of people have this problem.  Restarting dbus-1 also fixes the situation for me, but what a pain!  Hopefully this will get fixed soon.

---

