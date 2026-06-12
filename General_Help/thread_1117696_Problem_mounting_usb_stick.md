---
title: "Problem mounting usb stick"
date: 2009-04-06
forum: General Help
---

### Post by Azdour on 2009-04-06
Hi All,

I'm using Ubuntu 8.04, and when I put in my Corsair stick into the USB port it does not automatically mount.

It appears in Nautilus as labelled as 'USB Drive' (but not as Corsair as it does on other machines). When I double click on it it shows an error dialog, "failed to mount, cannot mount file".

It's there in /dev - sdb and sdb1. I can see it in lshal as sdb and it's correctly identified it as Corsair. It just will not auto mount it.

I've looked in dmesg, daemon log and syslog files and cannot see any hal messages that would give me a hint at what the issue is.

I can mount it as sudo but I do not want to give sudo access to the user account I'm logged into.

Anyone any ideas of what to try or where to look.

It looks like HAL detects the device, but never mounts it, so I'm not sure if it's a HAL issue or the underlying gnome mount?

---

### Post by aaronp on 2009-04-14
you may need to use sudo access to mount the drive but that doesn't necessarily mean that root access persists.
sudo only works for that command (or terminal session) so if you mount it with the proper permissions the user will still not have root access.

---

### Post by Azdour on 2009-04-20
Hi,

Thanks for the reply. I'd like to try and solve it so that the user doesn't keep pestering me when they want to mount the usb :), and they are not that command line savvy.

My latest findings are:

HAL detects the Corsair USB stick, lshal contains the same info on the Corsair as a listing produced on another machine that mounts it correctly.

Via the terminal, gnome-mount successfully mounts it as the user.

So... I'm not sure of the process of detection and mounting devices. Does HAL detect and use gnome-mount to mount it? In which case it looks like the communication between HAL and gnome-mount is not working.

---

### Post by battleshipterry on 2009-04-20
This is cut and paste from my other post and u guys are way more advanced then me but maybe this will add help. I found I was not able auto mount a USB stick it said this error when I pluged it in.

cannot mount drive
cannot obtain lock on media .hal-mtab ubuntu

I had the above error show up when I tried to mount a different drive (additional drive and/or USB stick drive) I searched for help but there was no recent data, but a old post on a different forum led me to a Wine problem so I uninstalled Wine and Ubuntu now mounts other drives.


PS I rebooted and reinstalled Wine and drives still work.

---

### Post by Azdour on 2009-04-22
Hmm... When I log in as other people on the machine the usb mounts correctly, so I'm not sure if it's a Wine issue.

Does anyone know where I can find the process of how usb sticks are detected through to their actual mounting? I believe something in the mounting process is detecting the device, but never gets to mount it. HAL detects its. gnome-mount mounts it if run by hand. So it's somewhere in-between that's the issue.

---

