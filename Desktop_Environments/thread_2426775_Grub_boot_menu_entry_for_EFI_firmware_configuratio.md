---
title: "Grub boot menu entry for EFI firmware configuration"
date: 2019-09-13
forum: Desktop Environments
---

### Post by Geoff_Lane on 2019-09-13
Folks,

I have a dual boot system with Ubuntu 18:04 being my main system and Windoz10 when I have to :cool:

Running sudo update-grub or update-grub2 I get the following output;

```
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-62-generic
Found initrd image: /boot/initrd.img-4.15.0-62-generic
Found linux image: /boot/vmlinuz-4.15.0-58-generic
Found initrd image: /boot/initrd.img-4.15.0-58-generic
Found linux image: /boot/vmlinuz-4.15.0-55-generic
Found initrd image: /boot/initrd.img-4.15.0-55-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
```

At boot I get the options for Ubuntu or Windoz and under advanced options have the other Kernel images but cannot see any option for the last entry for EFI firmware configuration.

Should this be a visible entry at boot time?

Geoff

---

### Post by oldfred on 2019-09-13
In grub.cfg you should see this (and only the menu entry part in grub menu), not sure it works on all systems, but it should take you into your UEFI/BIOS:
```

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###
```

---

### Post by Geoff_Lane on 2019-09-18
> **oldfred said:**
> In grub.cfg you should see this (and only the menu entry part in grub menu), not sure it works on all systems, but it should take you into your UEFI/BIOS:
```

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###
```

Thank you, practicing with GRUB now on an external drive, that is causing me issues too as it lists everything on my internal drive too :o

Geoff

---

### Post by oldfred on 2019-09-18
I have multiple installs, so I turn off os-prober and add only those I want into 40_custom.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
Some examples:
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

