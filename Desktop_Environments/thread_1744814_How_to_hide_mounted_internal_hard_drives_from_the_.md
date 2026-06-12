---
title: "How to hide mounted internal hard drives from the launcher."
date: 2011-04-30
forum: Desktop Environments
---

### Post by bhishan on 2011-04-30
Is there a way to hide the mounted internal hard drive partitions from the launcher? I do not want to hide usb drives though. I am using Ubuntu 11.04.

---

### Post by coffeecat on 2011-04-30
Yes. Mount them in mountpoints in /mnt rather than in /media. You will get neither a desktop icon nor a launcher icon.

This obviously means mounting them by means of entries in /etc/fstab or manually from the terminal, rather than using Places in Nautilus which will automount them in /media.

**EDIT**: to clarify. You can mount them anywhere but in /media to not have icons on the desktop or in the launcher. You could make special mountpoints directly in the root of the filesystem if you so wish. I simply mentioned /mnt because that is a convenient place.

---

### Post by prab97 on 2011-05-01
Doesn't work for me. I mounted the drives in separate directories in my home directory, but still they appear in the launcher.

---

### Post by coffeecat on 2011-05-01
> **prab97 said:**
> Doesn't work for me. I mounted the drives in separate directories in my home directory, but still they appear in the launcher.

That is true, mounting partitions in /home will do the same as mounting in /media. Create a mountpoint in /mnt or in the root of the filesystem and you will **not** get a launcher or desktop icon. I know that many people use folders in home as mountpoints for internal partitions but this is not particularly good practice. That is what /mnt is for.

---

### Post by bhishan on 2011-05-02
> **coffeecat said:**
> That is true, mounting partitions in /home will do the same as mounting in /media. Create a mountpoint in /mnt or in the root of the filesystem and you will **not** get a launcher or desktop icon. I know that many people use folders in home as mountpoints for internal partitions but this is not particularly good practice. That is what /mnt is for.

Can you please provide details (what to type in the terminal) on how to do this. I want those drives to be mounted automatically when I start the computer but not show up in the launcher.

---

### Post by Hreinsi on 2011-05-02
Take alook here.
[http://www.webupd8.org/2011/04/how-to-remove-mounted-drives-from.html](http://www.webupd8.org/2011/04/how-to-remove-mounted-drives-from.html)

To hide all

gsettings set com.canonical.Unity.Devices devices-option "Never"

in Terminal

---

