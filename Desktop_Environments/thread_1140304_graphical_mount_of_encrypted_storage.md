---
title: "graphical mount of encrypted storage"
date: 2009-04-27
forum: Desktop Environments
---

### Post by StefanX on 2009-04-27
I am using a dm-crypt+LUKS encrypted USB harddisk for several years. When connecting the drive a window appears prompting for the password. After entering the password the storage is mounted automatically. This drive is formated with ext3.

Now I bought a new eSATA harddisk which is encrypted the same way. When connecting the harddisk I don't get any prompts. Also the drive is not listed in gnome menu. Instead I have to unlock and mount the storage manually in the console (with cryptsetup and mount). This drive is formated with ext4.

I don't have any entries for these drives in /etc/fstab.

Any idea how to get a prompt and auto mount for the second drive? Any help is really appreciated!

---

### Post by Martin von Wittich on 2009-06-16
Same issue here... eSATA looks like an internal disk to the computer, and g-v-m seems to ignore fixed disks :(

---

### Post by Martin von Wittich on 2009-06-16
It's a bit easier by changing the PolicyKit settings  org.freedesktop.hal.storage.{crypto-setup,mount}-fixed to Active Console = yes. Then I can issue

$ gnome-mount /dev/sda1

and it will prompt me for my password (haven't tested yet whether it actually saves it) and it doesn't require root any longer.

---

