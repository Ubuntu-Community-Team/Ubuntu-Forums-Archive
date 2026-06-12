---
title: "Stopping fstab entries causing maintenance shell?"
date: 2009-01-17
forum: General Help
---

### Post by ryukent on 2009-01-17
Quick question for anyone who knows...

I've made an entry in my fstab that references a USB hard disk by UUID. I've done this so that when I attach the device, it always mounts the volumes to the place I want them mounted and with the correct options. I don't like the automatic mount location.

Problem is, when the system automounts at boot and finds that the device is not attached, it launches a maintenance shell and interrupts boot until ctrl+d has been hit.

Does anyone know a way that I can specify an entry in fstab to be ignored at boot if the device is not attached?

---

### Post by dcstar on 2009-01-17
> **ryukent said:**
> Quick question for anyone who knows...

I've made an entry in my fstab that references a USB hard disk by UUID. I've done this so that when I attach the device, it always mounts the volumes to the place I want them mounted and with the correct options. I don't like the automatic mount location.

Problem is, when the system automounts at boot and finds that the device is not attached, it launches a maintenance shell and interrupts boot until ctrl+d has been hit.

Does anyone know a way that I can specify an entry in fstab to be ignored at boot if the device is not attached?

Option "noauto", or simply put a disk label on your USB device partitions and they will always be mounted using those label names.

---

### Post by ryukent on 2009-01-18
Sorry, but I of course tried both of those before posting. noauto option will still cause a maintenance shell if you reference by UUID. Setting a disklabel only suggests to Ubuntu where might be a good place to mount. If you already have folders there with permissions set up etc, then it will mount at "Removable1_" instead of "Removable1". I need to have entries in the fstab in order to set character sets, but the device will not always be present. I need it to not halt boot when the device isn't connected. Is there any way of doing this?

---

### Post by bill_mcgonigle on 2009-04-13
I'm using shell scripts in this situation.  Ugly!  We need something like 'noauto' that won't flunk on a missing block device.

anyway:

if [ -b /dev/md6 ]; then
   /sbin/mount /dev/md6 ...
fi

the md subsystem seems more tolerant of missing devices.  You could setup a mirror with one 'missing' drive if you only have one.  But this is so ugly it hurts, so maybe somebody knows a better way.

---

