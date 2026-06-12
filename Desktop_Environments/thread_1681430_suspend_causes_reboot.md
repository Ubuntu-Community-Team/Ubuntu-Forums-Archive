---
title: "suspend causes reboot"
date: 2011-02-04
forum: Desktop Environments
---

### Post by svaens on 2011-02-04
Another day, another regression. 

I can get into suspend, but getting out adds an element of surprise; sudden reboot! (without any of the niceties of unmounting filesystems, etc).

Fortunately I found a fix in the archives for the beta version of maverick:

[http://ubuntuforums.org/showthread.php?t=1586178&page=5](http://ubuntuforums.org/showthread.php?t=1586178&page=5)

I have a Sony Vaio VPCEB1Z1E and passing the option acpi_sleep=nonvs to the kernel solved the issue of rebooting instead of resuming from suspend. As you can read here problems started when was introduced (in 2.6.35-rc4) saving NVS area during suspend:
[http://www.spinics.net/lists/linux-acpi/msg29521.html](http://www.spinics.net/lists/linux-acpi/msg29521.html)

So you need to modify /boot/grub/grub.cfg to pass that option to the kernel, like this:
Code:
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set 5ae3fe0b-ef15-4af0-a452-71b09868467f
        linux   /boot/vmlinuz-2.6.35-22-generic root=UUID=5ae3fe0b-ef15-4af0-a452-71b09868467f ro   quiet splash acpi_sleep=nonvs
        initrd  /boot/initrd.img-2.6.35-22-generic
}


I have a sony vaio, VGN-FW35G,
with ATI graphics, and intel processor.

Is it only us lucky sods using vaio's that get this new feature? 
Or is it generally available?

Any one else had this problem?

---

