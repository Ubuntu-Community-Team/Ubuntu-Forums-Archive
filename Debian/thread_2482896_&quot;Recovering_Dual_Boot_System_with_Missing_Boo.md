---
title: "&quot;Recovering Dual Boot System with Missing Bootloader and 'grub_efi_secure_boot' Error"
date: 2023-01-13
forum: Debian
---

### Post by nivdh on 2023-01-13
I am having an issue with my dual boot system, which consists of Parrot OS and Windows. Recently, I had a problem with my system boot order where it was showing "*operating system could not be loaded because required file is missing or contains errors*." The issue occurred because I did not properly shut down my laptop and did not charge it. I checked my UEFI boot order and it was showing Parrot and Windows bootloader, but after two shut downs it was only showing Windows. I tried to use the bcdedit command to create a copy of the Windows boot loader and edit it to point to the Parrot EFI, but it still showed the same error.

when i did the bcdedit command it shows parrot in the windows boot manager but when i selected it the output was this [![bcdedit][1]][1]

I then tried to install another copy of Parrot OS alongside it, but it is not showing up in the UEFI boot order. Now, I have to manually select the EFI and load the GRUB file to enter the new OS. I am wondering if it is possible to recover my first Parrot OS and if it is possible to make the new OS show up again in the boot order. I also tried to get into the old Parrot OS by using the recovery mode in the new Parrot OS (GRUB command line), but it showed an error message saying *command 'grub_efi_secure_boot' not found*.
[![old parrot os][2]][2]

 Can anyone help me sort out this issue?


i also used boot repair tool and it generated a report
[[https://paste.ubuntu.com/p/VkBjvBGFSn/]](https://paste.ubuntu.com/p/VkBjvBGFSn/])[3]


  [1]: [https://i.stack.imgur.com/mEzND.jpg](https://i.stack.imgur.com/mEzND.jpg)
  [2]: [https://i.stack.imgur.com/rA5Wr.jpg](https://i.stack.imgur.com/rA5Wr.jpg)
  [3]: [https://paste.ubuntu.com/p/VkBjvBGFSn/](https://paste.ubuntu.com/p/VkBjvBGFSn/)

---

### Post by oldfred on 2023-01-13
Do not know btrfs and how its sub-volumes work. 

You show grub installed in old BIOS boot mode to MBR and in ESP for UEFI boot. 
Since UEFI system with Windows in UEFI boot mode, you must always boot in UEFI boot mode and have system set to default boot in UEFI mode. 
And when booting live installer always choose the UEFI boot option.

If install in sda4 is the install you want, then Boot-Repair's default reinstall of grub in UEFI mode and then boot of system in UEFI mode should work.
If install in sda5 is what you want, you need to use Boot-Repair's advanced mode where it lets you choose which install to use as default. 
Not sure with btrfs, if you are getting both installs as grub boot options, but you should be able to choose old install and from inside it, just reinstall grub.

---

