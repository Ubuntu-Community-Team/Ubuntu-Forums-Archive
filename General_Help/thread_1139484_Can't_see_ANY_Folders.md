---
title: "Can't see ANY Folders"
date: 2009-04-27
forum: General Help
---

### Post by EyeHustle on 2009-04-27
I have about 2 hours experience with ubuntu. (and linux all together as well) and i am using virtualization with virtual box. I connected a WD external USB hard drive and my Linux box does not see any folders in a certain section. How could this be? I can see ALL other folders and files in the entire hard drive except in one particular folder. What would cause this?

---

### Post by EyeHustle on 2009-04-28
Any Ideas?

---

### Post by freonchill on 2009-04-28
linux hides folders that start with "." or ".."
in nautilus hit CTRL+H

or in terminal rather than typing "dir" or "ls" type "ls -al"

---

### Post by drs305 on 2009-04-28
> **EyeHustle said:**
> I have about 2 hours experience with ubuntu. (and linux all together as well) and i am using virtualization with virtual box. I connected a WD external USB hard drive and my Linux box does not see any folders in a certain section. How could this be? I can see ALL other folders and files in the entire hard drive except in one particular folder. What would cause this?

You may need to clarify *ANY*. Any on the USB device, any in VB, any in the system partition, any hidden files, etc.

Can you see other folders on the USB device? If not, search for how to set up USB devices in linux. Also make sure you have USB enabled in VB in the machine's Settings section.

Is this folder on the same partition as all the rest?

Can you 'see' it via the command line? "ls -la /path/to/folder"

Does it have the same permissions as all the rest? (Check with above command if it finds the specific folder you are interested in.)

If this is from within Vbox, is this folder included in the "Shared Folders"? From the main virtualbox menu, highlight the machine, select Settings from the top menu, then scroll down on the right side to Shared Folders. If it isn't listed, double-click shared folders and add it (if VB can see the folder).

---

### Post by EyeHustle on 2009-04-28
Thanks, all good suggestions. I have to wait til' i get back to the machine. and I'll try all of it.

---

### Post by EyeHustle on 2009-04-28
now, when i connect the drive to my physical computer it says it's unable to mount the drive. where as it was mounting the drive before hand. what's going on?

---

### Post by EyeHustle on 2009-04-28
Ok, got some details. Here is the exact error I get

   Error org.freedesktop.Hal.Device.UnknownError.
  Details: libhal.c 1399 : wrong reply from hald. Expecting an array.
  org.freedesktop.Hal.Device.Volume.UnknownFilesystemType
  

Please Help!

---

