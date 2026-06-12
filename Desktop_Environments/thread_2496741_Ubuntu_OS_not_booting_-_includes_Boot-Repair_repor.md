---
title: "Ubuntu OS not booting - includes Boot-Repair report"
date: 2024-04-10
forum: Desktop Environments
---

### Post by jdias5 on 2024-04-10
I installed successfully, some years ago, a Ubuntu Desktop 22 LTS in a bootable SSD on a Intel i5 Desktop System. This system was only sometimes in usage.

Now, when I switch on my Desktop, the BIOS don't see the the SSD, only the CDROM. However, if I boot the computer from an Installation CD of Ubuntu 22.04 LTS, I have access to the SSD, mounted in a ad-hoc location.

Also, I phoned the montherboard manufacturer, that said to me that if the SSD isn't shown, the problem would be probably that the boot partition was corrupted.

I ran Boot-Repair, and it produced the report in [https://paste.ubuntu.com/p/vZpPvchhkX/](https://paste.ubuntu.com/p/vZpPvchhkX/)   

Thus, I am asking to the experts on Ubuntu what should be the repair procedure. Should I try with the recommended repair on the pastebin I indicated?

Thanks

---

### Post by grahammechanical on 2024-04-10
> Now, when I switch on my Desktop, the BIOS don't see the the SSD, only the CDROM

What does that mean?

a) When you boot the computer you get an error message saying no operating system found.

or

b) When you enter the BIOS/UEFI settings utility and open the boot manager section the SSD is not listed.

In the BIOS/UEFI boot manager section is the SSD enabled/activated?

Regards

---

### Post by oldfred on 2024-04-10
You have an UEFI system.
You have grub installed in MBR for old BIOS boot and grub in the ESP - efi system partition for UEFI boot.
And you have the very old MBR(msdos) partitioning. Ubuntu allows this with UEFI, but probably should not.
The only time MBR is required is for older systems that boot Windows in BIOS mode.
Microsoft requires gpt partitioning with UEFI boot.

You do not show an ubuntu entry in UEFI boot menu. starting at line 51.
It looks like Boot-Repair is suggesting the full reinstall of grub in UEFI boot mode, which would add an entry in UEFI to boot Ubuntu.

Make sure UEFI system settings have UEFI as default boot mode.
And always choose to boot USB flash drives in UEFI boot mode.

Would be better to eventually convert to gpt, but MBR to gpt totally erases entire hard drive, so good backups required or starting over  when you get new drive.

---

### Post by jdias5 on 2024-04-11
1. When I access BIOS, the CDROM is listed, but the SSD is not listed.
2. When I boot the computer without a CDROM in it, the system doesn't boot. Says something like: "Insert a boot device and press a key..."
3. The computer was assembled in 2019, with recent hardware.
4. In BIOS, the 6 SATA 6G are set to be discoverable, but not hot-pluggable. As I said, only the CDROM lists here, as in the boot menu of BIOS

Thanks

---

### Post by oldfred on 2024-04-11
When you say UEFI/BIOS are you referting to boot menu or system settings?
System must show drive as Boot-Repair report shows it.
And Ubuntu entry is missing from UEFI boot menu.

Make sure UEFI settings are set to UEFI only.
If you try to boot in old BIOS mode, the grub in MBR will not work.

---

### Post by jdias5 on 2024-04-11
I have changed the BIOS settings, enabling "UEFI only" for "Launch CSM\Boot Device Control" and "Launch CSM\Boot from Storage Devices".

However, the BIOS presents the same problem: the SSD is not listed, and only the CDROM is listed.

Note: now if no CDROM is inserted, the system opens the BIOS window.

Should I go for the Boot-Repair recomendation?

Thanks

---

### Post by tea for one on 2024-04-11
> **jdias5 said:**
> Should I go for the Boot-Repair recomendation?
Do you have a backup of your personal data?

---

### Post by jdias5 on 2024-04-11
Yes I think, but I would not like to reformat the disk to start an installation from scratch.

In fact, my system worked well until some weeks (months?) ago.

---

### Post by tea for one on 2024-04-11
Starting from scratch would, actually, be a sound idea.
You could then format your disk with GPT and install in UEFI mode - a modern approach.

Anyway, if you are reluctant to do this, let boot-repair do its magic.
You have a backup, which is the most important ingredient.

---

### Post by jdias5 on 2024-04-11
I have tried the Boot-Repair recommendation. The report is in [URL="https://paste.ubuntu.com/p/z5pYfP7nFH/"]https://paste.ubuntu.com/p/z5pYfP7nFH/

[/URL]However, after setting to UEFI only the whole CSM menu: Boot from Storage Device, Boot from Network, etc., neither the computer boot from the SSD, nor, after accessing the BIOS, detects the SSD at all. When I access the SATA 6G list of devices, only the CDROM is there, not the SSD.

Thanks

---

### Post by tea for one on 2024-04-11
Boot-repair can see your disk (line 114) but it's invisible to your UEFI settings - quite unusual.

Line 57 - Warning: NVram is locked (Ubuntu not found in efibootmgr).
We've seen this reasonably often and there doesn't seem to be one solid answer.

Can you access your UEFI settings and disable these options (if they are present):-
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Or similar settings with Trust.

Then, try boot-repair again.

---

### Post by jdias5 on 2024-04-12
Unfortunately, my BIOS doesn't have such options. However, I set all the Boot Devices (Storage, Network, ...) to UEFI only.

Is it a possibility to reinstall Ubuntu from a CD (22.04 LTS), preserving the data partition (/dev/sda5), and only reformatting and resetting the boot partition?

Did boot-repair do that?

Thanks?

---

### Post by oldfred on 2024-04-12
What brand/model system? some have specific settings in UEFI settings.

Note sure if anything works as long as you have locked NVRAM.

I also show an error on modprobe, 
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/ISO**[/COLOR][COLOR=#000000]$ modprobe efivars [/COLOR]
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-27-generic
[/FONT]
```

But efivars is really here (really a directory,so this does not list anything):
cat /sys/firmware/efi/efivars

I believe there is some change on location of efivars with different versions of some software.

Some work arounds
Locked NVRAM - turning on Secure boot & reset UEFI Dell XPS 9530
[https://ubuntuforums.org/showthread.php?t=2490359](https://ubuntuforums.org/showthread.php?t=2490359)
Locked UEFI/BIOS setting: Lenovo UEFI screen
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
add "--no-nvram" to the "grub-install" command 
[https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0](https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0)

---

### Post by jdias5 on 2024-04-12
My system was assembled by me, with a ASUS Prime motherboard, and a SSD Kingston A400 480 Gb. The system is dated from about 2019.

After booting with the Ubuntu Installation CDROM, I run the SMART Data & Self Test: I made a short test, that said that "Disk is OK", and showed several parameters, e.g., "196 - Rellocation Count" with value "0".

I also run `badblocks`on `/dev/sda` which reported 0/0/0 errors.

Then I run `fsck`:

`sudo fsck -r -s -V /dev/sda`said, e.g:
```
ext2fs_open2 : Bad magic number in super-block
fsck.ext2 : Superblock invalid, trying backup blocks...
fsck.ext2 : Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem. If the device is valid and it really contains an ext2/ext3/ext4 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck ...

Found a dos partition table in /dev/sda
```

Doing the same for `/dev/sda1`gave no errors.

In fact, when I open the BIOS console (UEFI BIOS), the SSD doesn't appear on the menu Advanced\PCH Storage Configuration:

There are 6 items in the menu referring to the 6 SATA 6G ports of the motherboard, but only one, the one with the CDROM is acknowledged, the SSD is not (maybe because is "not bootable???? but it is very strange").

Also in the menu Advanced\HDD/SSD SMART Information, the device is not listed in the dropdown. There are only 6 items saying "N/A".

Thanks

---

### Post by oldfred on 2024-04-12
You cannot run fsck on a drive like sda, only on formatted partitions. 
And fsck is for Linux ext2, ext3, or ext4 formats. Different tools for other formats.

Suggest a full chroot into your install & reinstall of grub.
But also mount the efivars partition which is not shown in the examples.
[https://ubuntuforums.org/showthread.php?t=2482909&p=14180936#post14180936](https://ubuntuforums.org/showthread.php?t=2482909&p=14180936#post14180936)
When in chroot
mount -t efivarfs none /sys/firmware/efi/efivars
grub-install

Boot-Repair walks you thru a mimimum chroot, you probably can use it, but mount the efivars before running the grub-install command.
Some example chroots
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.

---

### Post by jdias5 on 2024-04-12
I tried to follow 
[https://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](https://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

After chroot and mounting, I did:

$ grub-install --recheck --no-floppy --force

Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported

$ update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-26-generic
Found initrd image: /boot/initrd.img-6.5.0-26-generic
Found linux image: /boot/vmlinuz-6.2.0-39-generic
Found initrd image: /boot/initrd.img-6.2.0-39-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
done

$ 

And did shutdown and reboot. The result was the same: the SSD doesn't boot.

I wasn't able to do: 
```
echo "configfile (hd0,gpt#)/boot/grub.cfg" > /boot/efi/ubuntu/grub.cfg
```

because no /boot/efi/ubuntu was there: no such directory.

---

### Post by oldfred on 2024-04-12
Did you mount the efivars when in chroot?

You cannot use #, but must use partition number  where grub is, either the one in the ESP, or the one in your install.

hd0,msdos1
You have old MBR(msdos) not newer gpt.
Better to not specify partitioning label whether gpt or msdos. Just use correct drive & partition.


If at grub terminal use ls to list partitions, then drill down to find grub.
ls
ls (hd0,1)/boot
And then whatever it shows in ESP.
or 
ls (hd0,5/boot
And then whatever it shows in your install.

---

### Post by jdias5 on 2024-04-13
Did you mount the efivars when in chroot? - Yes, I did.

Meanwhile, I don't manage to execute commands like `ls (hd0,1)/boot`. Gives an error. What do you want to say with this command.

My motherboard is optimized for Windows, I think... Although, I have successfully logged in in my system, now it doesn't boot...

---

### Post by VMC on 2024-04-13
What does just a '**ls**' show? It should show the partitions available.

---

### Post by jdias5 on 2024-04-18
To solve the problem, I tried to reinstall my Ubuntu Desktop 22.04 system, creating a new set of partitions, mostly automatically, and then erasing the disk.

However, after I completed the task, and rebooted the system, the motherboard didn't acknowledge the SSD with the OS. I had to reconnect the wires inside my desktop (I had already did something similar just after the appearance of the boot problem).

Then, when I switched on the system, it recognized the SSD in the BIOS, and was able to  boot. Despite the hardware intervention, I didn't understand why this happened. Maybe it was only the SATA ports where the SSD and the CDROM were connected, or the power cable of the SSD.

Thanks

---

