---
title: "Trouble Booting GRUB Automatically from Portable USB Drive"
date: 2024-02-22
forum: Debian
---

### Post by likimate on 2024-02-22
Hello everyone,

I'm encountering an issue with booting GRUB automatically from a portable USB drive, and I could use some assistance in troubleshooting it.

Here's the situation: I've installed Debian on a removable USB drive with three partitions - `sdb1` for EFI, `sdb2` for `/boot`, and `sdb3` as a LUKS encrypted drive for the root filesystem. I've configured the system to boot from the USB drive, and I can manually select it from the boot menu. However, instead of loading GRUB automatically, it takes me directly to the GRUB screen of my main OS.

Here's what I've tried so far:
1. Reinstalled GRUB from a live system and updated the configuration without any other drive connected to the system.
2. Verified that GRUB is installed correctly on the EFI partition (`/boot/efi` on `sdb1`) and that the configuration points to the correct partitions and paths.
3. Checked the UUIDs in `/etc/fstab` to ensure they match the corresponding partitions.
4. Confirmed that Secure Boot is not enabled on the system.
5. Tried adjusting the boot order in the BIOS/UEFI settings.

Despite these efforts, I'm still unable to boot into GRUB automatically from the USB drive. The issue also persist among different systems.

Interestingly, when I manually select the EFI file (`grubx64.efi`) from the boot menu, it loads GRUB without any issues.

I'm puzzled by this behavior and would appreciate any insights or suggestions on how to resolve it. Could there be something I'm overlooking in the GRUB installation process or the system's boot configuration?

If anyone has experienced a similar issue or has expertise in troubleshooting GRUB boot problems, I'd be grateful for your help. Thank you in advance for any assistance you can provide.

EDIT: I have created multiple copies of the system on different usb drives and a diskimage of it on my harddrive, so I am ready to try any idea on how to resolve this problem.

Best regards,
Likimate

---

### Post by coffeecat on 2024-02-22
*Thread moved to **Debian** sub-forum*.

---

### Post by oldfred on 2024-02-23
Ubuntu's install of grub always goes to first drive.
I only experimented once with Debian, just to see if I could install grub to sdb, rather than Ubuntu's default of first drive. And it worked, so I know Ubuntu installer is issue, not grub.

External drives with UEFI always boot using /EFI/Boot/bootx64.efi. And you choose that from UEFI one time boot menu.
Most UEFI systems remove a UEFI boot entry or modify it when a drive is unplugged. So if you installed & it created a Debian or grub entry, that may not be a correct UEFI boot entry when drive is unplugged.

I pretty much have Kubuntu on many drives, both external & internal. I can boot all external from UEFI boot menu using the /EFI/Boot/bootx64.
But usually use a grub boot stanza in my system to boot external drive from grub menu. Sometimes I have to edit grub as I boot as drive in boot stanza is not correct or change hd0 to hd1 or vice-versa, I now prefer labels. Depends on if I also have another drive plugged in and drive order that UEFI has defined.

examples from cavfan
[https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046](https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046)
Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)


I still have multiple larger flash drives with full installs, but now prefer SSD for external boot. My latest is a SSK USB to NVMe adapter.
```
menuentry 'SSK noble' {
search --set=root --label ssk-noble
configfile /boot/grub/grub.cfg 
}



```

---

