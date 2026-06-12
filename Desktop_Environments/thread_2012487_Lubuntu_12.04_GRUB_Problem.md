---
title: "Lubuntu 12.04 GRUB Problem"
date: 2012-06-29
forum: Desktop Environments
---

### Post by Queosar on 2012-06-29
Hello

I am trying to install Lubuntu 12.04 64-bit onto my Lenovo X121e notebook. Unfortunately it appears to fail when installing the bootloader. When it says 'installing the grub2 package'it fails & displays the following message:

The 'grub-efi' package failed to install into /target/. Without the GRUB bootloader the installed system will not boot.

The X121e contains a 128GB SSD. I have successfully installed Xubuntu, Ubuntu & Kubuntu 12.04 with no hassles. I have been using guided partitioning...do I need to do it manually?

Any help would be much appreciated.

Thanks
Queosar

---

### Post by MG&amp;TL on 2012-06-29
Since Lubuntu is no different under the hood than any of the other *buntus, I think your install media is probably corrupted, or you've got a bad disk.

Did you checksum your image?

---

### Post by Queosar on 2012-06-29
Hi MG&TL, thanks for the quick reply.

I have just loaded Xubuntu on again with no issue. I'll try re-downloading the Lubuntu image I suppose.

Thanks

Queosar

---

### Post by black veils on 2012-06-29
> **Queosar said:**
> Hi MG&TL, thanks for the quick reply.
I'll try re-downloading the Lubuntu image I suppose.


[SIZE=2][COLOR=Black]_**verify .iso integrity**_[/COLOR][/SIZE]

scroll down to **MD5SUM with "Checksums calculator" **
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Queosar on 2012-06-29
Thanks for the link. The MD5 checks out fine on the iso.

---

### Post by oldfred on 2012-06-29
Is this a UEFI system? It should not be installing grub-efi if in BIOS mode.

Both Windows & Ubuntu have two ways to boot now from CD or USB. One is the old BIOS and the other is the new UEFI. 
If you boot the efi verision it expects an efi partition and gpt(GUID) partitioning to install grub2 efi boot loader and you use UEFI to boot. 
If you boot the installer in MBR(msdos) mode it installs grub2 to the MBR and boots in BIOS mode.

Windows only installs to gpt partitioned drives with UEFI, but Ubuntu can be installed to gpt drives with BIOS, but grub needs an extra 1MB bios_grub partition for part of grub - core.img that is normally installed just after the MBR as that does not exist in gpt partitioned drives. gpt is suggested for SSD unless you have BIOS and want Windows also.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Queosar on 2012-06-29
Hi Fred, I think you're on to something. I'll have a play around with the UEFI settings. :)

---

