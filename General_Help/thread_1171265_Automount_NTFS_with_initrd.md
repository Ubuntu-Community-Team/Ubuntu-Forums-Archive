---
title: "Automount NTFS with initrd"
date: 2009-05-27
forum: General Help
---

### Post by bglinux on 2009-05-27
I've made custom live USB with minimal Ubuntu 9.04 distribution on it. I would like to have my NTFS partitions automatically mounted by the initrd image before the system is started. I will user the mounted partition as recovery option if the system does not boot successfully so I could write some information to a file located on it from the minimal environment in the initrd.

I've tried addting this information to my initrd.gz init file with no luck:

```
mkdir -p /media/windows
mount -t ntfs-3g -o defaults,locale=en_US.utf8 /dev/sda1 /media/windows

```Anybody has any idea how to automatically mount my NTFS partition with write access.

Thank you in advance!

---

### Post by rCXer on 2009-05-27
I'm kinda a newbie but here's what I did to automount a drive.  

* Install the "Storage Device Manager," a GUI that edits the /etc/fstab file.
```

sudo apt-get install pysdm

```

* Run it by going to System -> Administration->Storage Device Manager.

* In the "Partition List" pane, on the left, click on the triangle next to your disk to get a list of partitions.

* Select the ntfs partition. It should be the one whose Type = ntfs in the "General Configuration" tab. (If it asks whether it should configure it now just click OK).

* Start the "Assistant" and check "The file system is mounted at boot time" and uncheck "Mount file system in read-only mode" (I don't remember which other boxes to check)

---

### Post by hal8000 on 2009-05-27
> **bglinux said:**
> I've made custom live USB with minimal Ubuntu 9.04 distribution on it. I would like to have my NTFS partitions automatically mounted by the initrd image before the system is started. I will user the mounted partition as recovery option if the system does not boot successfully so I could write some information to a file located on it from the minimal environment in the initrd.

I've tried addting this information to my initrd.gz init file with no luck:

```
mkdir -p /media/windows
mount -t ntfs-3g -o defaults,locale=en_US.utf8 /dev/sda1 /media/windows

```Anybody has any idea how to automatically mount my NTFS partition with write access.

Thank you in advance!


Those commands are terminal commands not initial ramdisk commands. Work on your booted USB system, modify the live environment fstab with the entry

/dev/sda1 /media/windows  defaults,locale=en_US.utf8 0 0

and that should automatically mount your NTFS system. Remember to include a line for each NTFS partition you want to mount. You need to make sure that your live USB system contains ntfsprogs so that the NTFS system can be mounted.

---

### Post by sandy8925 on 2009-05-27
yeah you can do what hal8000 said. using the uuid to identify the drive is much better though.

---

### Post by bglinux on 2009-05-28
Thanks for the tips, guys!
Here is a detailed description of what I am trying to achieve:
1. I have build custom Ubuntu distro using this guide: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch) I have only installed debootstrap, xorg and some other software.
2. This distro is meant to be used on many machines with different hardware profiles and Windows XP or Vista installed and Grub4Dos on their boot partition (some of my machines have buggy BIOS and will never boot from USB). Grub4dos will boot the live system from the USB flash.
3. vmlinuz and initrd.gz are copied to the NTFS partition and I have two menu.lst files there (menu.lst: the default one to boot without any prompt into Ubuntu from the USB and menu.lst-win: the other one to boot into Windows).
4. I need to be able to write some information on the NTFS partition before the live USB is booted.

Thank you for you great support!

---

