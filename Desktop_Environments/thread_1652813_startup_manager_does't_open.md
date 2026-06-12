---
title: "startup manager does't open"
date: 2010-12-25
forum: Desktop Environments
---

### Post by kerana on 2010-12-25
I wanted to change the grub options so i installed startup manager. but when i try to run it this comes up:

Found linux image: /boot/vmlinuz-2.6.35-24-generic
ga
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
Grub2 detected
Usplash not detected
Splashy not detected
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)

what is wrong? do i need to install other things like Usplash to make it work?

---

### Post by hhh on 2010-12-25
It looks like that program started crapping out on recent Ubuntu versions...
[http://ubuntuforums.org/showthread.php?t=1608997](http://ubuntuforums.org/showthread.php?t=1608997)

What is it your trying to configure in Grub2? There is some decent documentation here...
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you want to remove the memtest options, in a terminal run```
sudo chmod -x /etc/grub.d/20_memtest86+
``` and then```
sudo update-grub
```
If you want to remove the recovery mode options, in /etc/default/grub remove the "#" from #GRUB_DISABLE_LINUX_RECOVERY=true
and then run ```
sudo update-grub
```

Be careful! Post back here if you are unsure.

---

