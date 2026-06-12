---
title: "What is the *proper* way in Ubunto to automount a partition?"
date: 2006-07-28
forum: Desktop Environments
---

### Post by xp_newbie on 2006-07-28
I have an NTFS partition that is not currently listed in /etc/fstab.
I would like it to be automounted there on boot.

I know how to modify the /etc/fstab file using a text editor, but is this the "Ubuntu way" of modifying this file? Isn't there a GUI front-end to it? If so, I would prefer avoiding manually editing this file as to not confuse the GUI tool.

My only problem is that I don't know which tool it is. Could someone please point me in the right direction?

Thanks!
Alex

---

### Post by rowanparker on 2006-07-28
AFAIK, you have to manually edit the /etc/fstab file.

---

### Post by Scythe!? on 2006-07-28
I've new to Ubuntu, had Dapper about a week. On first boot, my Windows partition was automounted and has been since. I have never changed settings or files.

---

### Post by gThree on 2006-07-28
I think this is possible in Kubuntu (/etc/fstab gets modified if you right-click and add a disk on your desktop), but don't know of any GUI method in Ubuntu.  Disk Manager just mounts/unmounts and I'm not aware of any other options.

---

### Post by xp_newbie on 2006-07-28
> **Scythe!? said:**
> I've new to Ubuntu, had Dapper about a week. On first boot, my Windows partition was automounted and has been since. I have never changed settings or files.

That's strange, because I installed Ubuntu on my laptop in a fashion similar to yours, so Ubuntu should have automatically placed my Windows partition in fstab. My Windows partition is NTFS (XP), is your NTFS as well? If not, perhaps that explains the difference.

If I use System > Administration > Disks to manually mount that partition, it mounts without any problem (on a /tmp subdirectory), but it doesn't remain mounted between boots.

I guess I will have to manually modify /etc/fstab.

Thanks.

---

### Post by dubbreak on 2006-07-28
> **gThree said:**
> I think this is possible in Kubuntu (/etc/fstab gets modified if you right-click and add a disk on your desktop), but don't know of any GUI method in Ubuntu.  Disk Manager just mounts/unmounts and I'm not aware of any other options.

I think you are correct about the disk manager. I added a partition to my computer and test mounted it with Disk Manager, then upon reboot the drive was not mounted, so I manually added it to fstab.

Wouldn't be hard to implement a radio or checkbox to automount a drive in the disk manager (parse and edit the fstab).. of course that may be too many features for the lean mean gnome guys ;-) (hint hint I'm alluding to the silly flame wars over not extending the functionality of the Screensaver Preferences).

---

