---
title: "Changing the default icons per filesystem type"
date: 2005-04-01
forum: Desktop Environments
---

### Post by cohort on 2005-04-01
Note there are alot of icons in the default gnome filesystem icon directory, from floppies to CDs to CF cards, but when I install a CF card in my system, it shows up using the 'hard drive' icon, and I'd rather it not.

Since I'm using a SanDisk usb card reader, and the device manager clearly shows it as such, can I change the default icon of anything hotplugged using that device upstream to the lovely CF card icon?

Yes, I've tried the 'custom icon' thingy, but that's not based on the disk contents, it's based on the mount point-which changes depending whether or not I hotplugged my usb keydrive first-so that's not a viable option.

---

### Post by kassetra on 2005-04-02
[QUOTE=cohort]Yes, I've tried the 'custom icon' thingy, but that's not based on the disk contents, it's based on the mount point-which changes depending whether or not I hotplugged my usb keydrive first-so that's not a viable option.[/QUOTE]

You most likely can have an auto-icon for that file type...
First you have to make sure you have an icon for the device in your theme's 48x48 (which is the default size for most monitors) devices directory - and it has to be named "gnome-dev-media-cf.png" - and also, you have to make sure that the device manager knows that the device is not just a standard block device.

---

### Post by cohort on 2005-04-03
[QUOTE=kassetra]You most likely can have an auto-icon for that file type...
First you have to make sure you have an icon for the device in your theme's 48x48 (which is the default size for most monitors) devices directory - and it has to be named "gnome-dev-media-cf.png"[/quote]
I switched my theme from the default 'Human' to the default Gnome almost the first day - I think it looks better, personally.  Indeed, the gnome device icons have all the icons I'm interested in using for my hotplug drives.

>  - and also, you have to make sure that the device manager knows that the device is not just a standard block device.
This is what I need to know how to do.  It says it knows what the adapter is (SanDisk ImageMate blah blah)..

I'm not a novice user, I just haven't been working with linux for desktop use until now.

---

