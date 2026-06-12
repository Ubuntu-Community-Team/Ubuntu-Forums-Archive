---
title: "Optiplex 320"
date: 2008-09-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kurdy86 on 2008-09-09
Hi All,

I installed Ubuntu on my desktop optiplex 320.
Now when i start i see a black screen with B and green kubus or whatever it is. Anyway i have seen alot of people have the same problem. I read the threads but i cant make it work. This is my first time i use linux. Can you please help me?
Thanks,

---

### Post by Kurdy86 on 2008-09-11
Thanks all..i installed opensuse 11
Bye bye Ubuntu

---

### Post by Suparious on 2008-09-11
For the purpose of this document, I am using a single SATA hard disk with the following partitions:

/dev/sda  - the block device
/dev/sda1 - the root "/" partition
/dev/sda2 - the extended partition (not relevant to this document)
/dev/sda5 - the swap partition (not relevant to this document)

1. Using the ubuntu live cd installer, perform a normal install WITHOUT REBOOTING. You will need to specify additional boot options for the kernel to boot properly:
```
pci=nomsi acpi=off
```

2. Once your install has completed, configure your network (or add your CD to the synaptic repositories).

3. Open a terminal window and perform the following to mount your installed hard disk to '/target' and add your device configurations to it:

```
# assuming you have a '/target' folder from the install.
mount /dev/sda1 /target
# lilo will not install without the following:
mount --bind /dev /target/dev 
mount -t proc proc /target/proc
# Root into the mounted filesystem
chroot /target
```

4. install 'lilo' and remove 'grub'

```
apt-get update
apt-get install lilo
apt-get remove grub
```

5. Configure your "/etc/lilo.conf" using the below as a guideline:

```
boot=/dev/sda
map=/boot/map
prompt
timeout=50
lba32
default=linux

image=/boot/vmlinuz 
label=linux
initrd=/boot/initrd 
read-only
root=/dev/sda1
append="quiet pci=nomsi acpi=off"

```

The most IMPERATIVE line to add here is: append="quiet pci=nomsi acpi=off"

6. install the lilo boot loader using:
```
lilo -b /dev/sda1
liloconfig
lilo -C /etc/lilo.conf
```

then reboot (cross fingers)

--------------------------
Troubleshooting

Q: it says that /target doesent exist or is not a valid mount point
A: create an empty folder called '/target' using ```
sudo mkdir /target
```

Q: When I try to install lilo using apt-get, it tells me that it is not found or that I cannot resolve the host.
A: Make sure you are online BEFORE chrooting to the /target (befire step 3). Because the LIVECD installer is already mounted, it seems that the repository on it isn't easily accessible (Or I am missing something to find it). If you have another CDROM you can use that as your repository too. THe easiest way, however, is to use the desktop tools (System->Administration->Network) and configure the internet.

last note. if you get any errors installing the boot loader, DO NOT reboot to 'try it out'. Google the errors and if you turn-up empty then post your questions here.

---

### Post by Suparious on 2008-09-11
Looks like I duplicated part of **Staceman**'s post here: [http://ubuntuforums.org/showpost.php?p=2463643&postcount=4](http://ubuntuforums.org/showpost.php?p=2463643&postcount=4)


-------

Infact, I have not found any linux that will install on the Dell Optiplex 320 without additional steps.

The reason SuSE can install using the installer and not Ubuntu, is because the Ubuntu installer doesn't give the option to use Lilo. Lilo is (to date) the only boot loader (besides windows) that will install on this Dell hardware series.

Dell is aware of the incompatible BIOS, however, admitted that no fix will be implemented for this problem either.

Perhaps the option for Lilo could be granted by Ubuntu once again.

---

### Post by fniessen on 2008-11-06
> **Suparious said:**
> 
Lilo is (to date) the only boot loader (besides windows) that will install on this Dell hardware series.

well grub2 is doing a good job here.

> **Suparious said:**
> 
Dell is aware of the incompatible BIOS, however, admitted that no fix will be implemented for this problem either.

Perhaps the option for Lilo could be granted by Ubuntu once again.
Dell has told me about grub2 (and guess grub is outdated cause of the new version of grub :grin:) but I absolute agree with you; Ubuntu should give the option to choose different bootloaders. (maybe on the alternate install cd ?)

---

