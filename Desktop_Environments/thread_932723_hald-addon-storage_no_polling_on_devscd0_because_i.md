---
title: "hald-addon-storage: no polling on /dev/scd0 because it is explicitly disabled"
date: 2008-09-28
forum: Desktop Environments
---

### Post by ngine13 on 2008-09-28
What does that mean?

I'm trying to solve the cd automount problem that i meet in gnome..

Please help me.. if you can. :)

---

### Post by ngine13 on 2008-09-28
maybe an easier question is :

why gnome-volume-manager can't automount a cd when is inserted..

hald is running

dbus is running..

what is the problem with cd automount..


p.s. 

1. usb automount is working
2. cd automount was working before some weeks!!!
3. cd automount is working when i leave a cd in the drive and i restart the system!!!

---

### Post by mikewhatever on 2008-09-28
Below is a quote from <man hal-disable-polling>:

> DESCRIPTION
hal-disable-polling  can  be used to to disable and enable media   detection on drives with removable storage. For more information about  both
the  big  picture  and  specific  HAL properties, refer to the HAL spec
which can be found in /usr/share/doc/hal-doc/spec/hal-spec.html depend&#8208;
ing on the distribution.


I saw powertop recommending it.

> Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.
In my case, running <sudo sudo hal-disable-polling --device /dev/cdrom> stops a window popping up when a cd is inserted, but no errors.

Can you post the output of the following please:
> cat /etc/fstab

---

### Post by ngine13 on 2008-09-28
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=cff704b2-8919-4b05-9b1a-3adba28dc109 /               reiserfs notail,relatime 0       1
# /dev/sda6
UUID=BA8A53316D4FAE83 /data           ntfs    defaults,umask=007,users,gid=46 0       1
# /dev/sda1
UUID=72b0e88e-464e-e79e-76ef-2e5fdf2f4f4f none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by mikewhatever on 2008-09-28
Well, as you can see, the cdrom line is commented out. You'll need to remove the '#' sign from the beginning of the last line in fstab.

> sudo cp /etc/fstab /etc/fstab-backup
gksudo gedit /etc/fstab

When done try running > sudo mount -a

---

### Post by ngine13 on 2008-09-28
Thank you very much!!! :)

I use the command you recommended in order to enable polling on my device :

sudo hal-disable-polling --enable-polling --device /dev/scd0


ps 

i think that gnome doesn't read the fstab file.
i left the /dev/scd0 line as a comment.
the output that bash gave me after executing the "sudo hal-disable-polling --enable-polling --device /dev/scd0" command is :

Polling for drive /dev/scd0 have been enabled. The fdi file deleted was
  /etc/hal/fdi/information/media-check-disable-storage_model_BD_ROM_BC_5500A.fdi

Thanks again. :)

---

### Post by mikewhatever on 2008-09-28
OK, but polling was probably disabled because the cdrom was unmounted. If you don't want to mount it manually, edit fstab as described above.

---

### Post by ngine13 on 2008-09-28
> **mikewhatever said:**
> OK, but polling was probably disabled because the cdrom was unmounted. If you don't want to mount it manually, edit fstab as described above.

But i don't mount it manually and it works.. with the /dev/scd0 fstab line as a comment. 

I mean i insert a cd in the drive and instantly in the gnome desktop appears a cdrom icon and a nautilus window with it's content.

I press then right click on the cdrom icon -> eject.

Then i put again the cd in the drive to check it and it works.

I can try to uncomment the line.. but nothing is going to change because i think than only when i use the command "mount" in a terminal i need that line uncomment.

Thanks again. :)

---

### Post by mikewhatever on 2008-09-28
I agree, if it works as is, don't fix it.

---

