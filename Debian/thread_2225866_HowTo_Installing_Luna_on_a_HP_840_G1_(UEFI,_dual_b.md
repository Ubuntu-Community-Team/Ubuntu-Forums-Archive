---
title: "HowTo: Installing Luna on a HP 840 G1 (UEFI, dual boot Win 8.1, Intel 7260-ac)"
date: 2014-05-23
forum: Debian
---

### Post by prmurthy on 2014-05-23
[SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]I had issues installing elementary on my new HP 840 G1 because my wired and wireless cards weren't recognized by the 3.2 kernel that comes with the Elementary Luna download ISO. [/COLOR][COLOR=#252C2F]I have an Intel 7260-ac mini-PCI card in my laptop. [/COLOR][COLOR=#252C2F]I also wanted to install it in UEFI mode, dual-booting into Windows 8.1[/COLOR]
[COLOR=#252C2F]I solved it using the below steps and thought it may be of use to someone. This may also work for similar other laptops. I have written this out based on my recollection of what I did. If there are any errors, please let me know and I am happy to update this.[/COLOR]
[COLOR=#252C2F]
Note: This doesn't install grub - you really dont need it and I found it ugly to go from the refind menu, then to grub and then onto booting the system. However, if you wish to install grub as well, then just adjust Step 3 to run ubiquity without the "-b" option. However, you will then need to run boot-repair once you have booted into elementary Luna because Luna doesnt install grub correctly into the EFI partition. in fact, I think it doesnt install grub-efi at all, but I dont know.[/COLOR]

[COLOR=#252C2F]1. Download 14.04 Trusty and create a bootable USB disk. Boot into 14.04[/COLOR]
[COLOR=#252C2F]Partition your hard disk and create your efi partition (512MB, FAT32) using gparted. Make sure you use gpt partitioning and also set the Boot flag on your EFI partition. I created a 512MB FAT32 EFI partition, a windows ntfs partition and a couple of ext4 partitions for Linux.
You could also use a gparted live CD, or anything else for the above.

[/COLOR]<At this point, I installed Win8 and upgraded to 8.1. I got this working fully. Nothing you do subsequently should impact this Win8.1 installation>

If you didn't stop by the WIndows 8.1 install above, continue below in UBuntu 14.04. If you did stop, then you will need to boot into UBuntu 14.04 again.
[COLOR=#252C2F]Open a terminal and type in[/COLOR][/FONT][/SIZE]```
[INDENT][SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]sudo mkdir /tempefi[/COLOR]
[COLOR=#252C2F]sudo mount /dev/sdaY /tempefi[/COLOR]
[COLOR=#252C2F]sudo mkdir /tempefi/pkg[/COLOR][/FONT][/SIZE][/INDENT]

```[INDENT][SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]where Y is your EFI partition

[/COLOR][/FONT][/SIZE][/INDENT]
[SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]2. Download the following and save it to the pkg folder in your efi partition. e.g. "sudo cp xxxx /tempefi/pkg"[/COLOR][/FONT][/SIZE][INDENT][SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]- linux-signed-generic-lts-trusty[/COLOR]
[COLOR=#252C2F]- linux-signed-image-3.13.0.24-generic[/COLOR]
[COLOR=#252C2F]- linux-signed-image-generic-lts-trusty[/COLOR]
[COLOR=#252C2F]- linux-headers-generic-lts-trusty[/COLOR]
[COLOR=#252C2F]- linux-headers-3.13.0-24-generic[/COLOR]
[COLOR=#252C2F]- linux-headers-3.13.0-24[/COLOR]
[COLOR=#252C2F]- sbsigntool[/COLOR][/FONT][/SIZE][/INDENT]
[SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]I dont recall the exact package names, but a bit of googling should find them.[/COLOR]
[COLOR=#252C2F]
3. Reboot laptop and set BIOS to boot in Legacy BIOS mode and install elementary without a bootloader. You can do this by selecting "Try out Elementary OS", and then typing "sudo ubiquity -b" in a terminal window.[/COLOR]
[COLOR=#252C2F]
4. See if it boots up. It is unlikely to, since there is no legacy bootloader installed. In any case, this is legacy mode, not UEFI. Your laptop may also refuse to recognize the presence of a hard disk, but don't worry.[/COLOR]
[COLOR=#252C2F]
5. Reboot and set the BIOS back to UEFI mode[/COLOR]
[COLOR=#252C2F]
6. Boot into 14.04 Ubuntu again using your bootable USB[/COLOR]
[COLOR=#252C2F]
7. As root, run the following in a terminal window[/COLOR][/FONT][/SIZE]```
[INDENT][SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]mount /dev/sdaX /mnt[/COLOR]
[COLOR=#252C2F]for i in /dev /dev/pts /proc /sys; do mount -B $i /mnt$i; done[/COLOR]
[COLOR=#252C2F]chroot /mnt[/COLOR][/FONT][/SIZE][/INDENT]

```[INDENT][SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]where X is your elementary root partition. e.g. mount /dev/sda5 /mnt. Replace sda with sdN if you have multiple disks.[/COLOR][/FONT][/SIZE][/INDENT]
[SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]
8. Once you are chrooted, type in:```
 sudo mkdir /tempboot && sudo mount /dev/sdaY /tempboot
``` 

9. Then install all the saved packages using "dpkg -i /tempboot/pkg/<pkg name>. This should install a new updated kernel in your elementary distribution. Also e[/COLOR][COLOR=#252C2F]dit /etc/fstab and add a line to mount /dev/sdaY into /boot (e.g. /dev/sdaY /boot ext4 defaults 0 0)[/COLOR]
[COLOR=#252C2F]
10. ```
sudo umount /tempboot
```[/COLOR]
[COLOR=#252C2F]
11. CTRL-D to log out of chroot and return to Ubuntu[/COLOR]
[COLOR=#252C2F]
12. In a terminal type in[/COLOR]
```
[COLOR=#252C2F]for i in /dev /dev/pts /proc /sys; do sudo umount /mnt$i; done[/COLOR]
```[COLOR=#252C2F]. You may get an error that /dev is busy - I ignored it.[/COLOR]
[COLOR=#252C2F]
13. Download reFind ([/COLOR][http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)[COLOR=#252C2F])[/COLOR]
[COLOR=#252C2F]
14. In a terminal type:[/COLOR][/FONT][/SIZE]```
[INDENT][SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]sudo mkdir /tempboot[/COLOR]
[COLOR=#252C2F]sudo mount /dev/sdaY /tempboot[/COLOR][/FONT][/SIZE][/INDENT]

```[SIZE=2][FONT=trebuchet ms]
[COLOR=#252C2F]
15. Install reFind using "dpkg -i <refind package name>". Then type, as root,:[/COLOR][/FONT][/SIZE]```
[INDENT][SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]cp -R /mnt/boot/vmlinuz* /tempboot[/COLOR]
[COLOR=#252C2F]cp -R /mnt/boot/init* /tempboot[/COLOR]
[COLOR=#252C2F]cp -R /mnt/boot/abi* /tempboot[/COLOR]
[COLOR=#252C2F]cp -R /mnt/boot/System* /tempboot[/COLOR]
[COLOR=#252C2F]cp -R /mnt/boot/config* /tempboot[/COLOR]
[COLOR=#252C2F]sudo umount /mnt
[/COLOR][/FONT][/SIZE][/INDENT]

```[INDENT][SIZE=2][FONT=trebuchet ms]
Now type in, as root, ```
 blkid 
``` and note down the UUID of /dev/sdaX (your root partition)
Using copy the below into a text file using an editor (e.g. gedit), replacing <myrootuuid> with the UUID of /dev/sdaX that you noted down above.```


```[/FONT][/SIZE]```
"Boot with standard options"        "ro root=UUID=*[FONT=trebuchet ms]<myrootuuid>[/FONT]*  acpi_backlight=vendor ipv6.disable=1 quiet splash "
"Boot to single-user mode"          "ro root=UUID=*[FONT=trebuchet ms]<myrootuuid>[/FONT] * quiet splash single"
"Boot with minimal options"         "ro root=UUID=[FONT=trebuchet ms]*<myrootuuid>*"
[/FONT]
```[FONT=trebuchet ms]
Save this file as refind_linux.conf in your current directory and then unmount the efi partition. We need to copy this into the efi partition so type in ```

cp refind_linux.conf /tempboot

```[/FONT]```
[FONT=trebuchet ms][COLOR=#252C2F]sudo umount /tempboot
[/COLOR][/FONT]
```

Note: the kernel options above (ipv6.disable=1 and acpi_backlight=vendor) are optional.
[/INDENT]
[SIZE=2][FONT=trebuchet ms][COLOR=#252C2F]
16. Reboot into your UEFI BIOS utility[/COLOR]
[COLOR=#252C2F]
17. Adjust the EFI executable which is run so it runs refind_x64.efi. In the 840 G1, I used the option of a Customized boot and set it to run \EFI\refind\refindx64.efi. Save and reboot.[/COLOR]
[COLOR=#252C2F]
18. Your elementary kernel should be available to boot[/COLOR]

[COLOR=#252C2F]Note: after booting, it is always good practice to run```
 sudo apt-get update && sudo apt-get dist-upgrade
```[/COLOR]
[COLOR=#252C2F]Optionally, you can dismount /boot, which will reveal the images installed on your root partition. You can delete everything under /boot AFTER UNMOUNTING /dev/sdaY

p.s. apologies to adamw for using the terms BIOS/UEFI with gay abandon. If you dont know what I am talking about, here is a great article: [/COLOR][/FONT][/SIZE][https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

---

