---
title: "Dual Booting Windows 10, Fedora 23 system broken (not UEFI)"
date: 2016-07-09
forum: Fedora/RedHat and derivatives
---

### Post by bbneo on 2016-07-09
I have a Dual  booting Windows 10 & fedora 23 system which had been working fine until I screwed up the boot  process when I let Boot-Repair on a booted Ubuntu external drive run on  the system (it was 32-bit Ubuntu if that matters).  
(I was tinkering with a 32-bit Ubuntu external USB drive to boot another older computer from...)

I have tried a BUNCH of things to fix this including running  Boot-Repair, tinkering with the activation and boot sector designations  in GParted, but still no joy... Right now I do have it working to boot  into Windows 10, but no Grub menu comes up to give me an option to start fedora instead.
When I try to run Boot-Repair (from a thumb drive),  I get:[INDENT][B]
"Please enable a repository containing the [grub2] packages in the  software sources of Fedora release 23 (Twenty (mapper/fedora-root). Then  try again."
[/B][/INDENT]

How am I going to do that if I can't get fedora 23 to boot in the first place?  

I do have a pastebin from Boot-Repair that I can share if anybody is  interested and knowledgeable:  [Analysis of HP dc5800]("http://paste.ubuntu.com/18886552/")

I don't want to "tinker" with any more of the various incantations I see  here and there for fear of making things worse [U]since I really don't  understand the whole "active partition, boot, grub" system/process in  the first place.
[/U]
Is there a good online reference to get a "bird's eye view" of how all of the boot pieces fit together?
 
[INDENT]**"active partition, boot, grub, OSes ..."**
[/INDENT]
 
Thanks in advance for any help or guidance.

---

### Post by oldfred on 2016-07-09
Boot-Repair with a full uninstall/reinstall of grub wants to download the latest version of grub for your install. So it needs your Fedora repository not the default in Boot-Repair.

But you should just be able to reinstall grub to MBR?
But I do not know LVM, normally you mount / (root) in LVM and /boot and install grub to MBR.
And to mount the LVM in /, you will need the lvm2 driver.
 sudo apt-get install lvm2 

This is typical Ubuntu LVM commands ( I do not use nor know LVM, just copied these & assume correct)

 sudo apt-get install lvm2
sudo vgchange -ay /dev/mapper/ubuntu--vg-root
sudo mount /dev/mapper/ubuntu--vg-root /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda 


Your root is this and your /boot is sda3?:
 /dev/mapper/fedora-root

With Windows 10 and dual booting you must keep Windows fast startup off. And on major Windows updates it will turn it back on.
      
 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Some users that have posted with systems that default to LVM installs often change to use standard ext4 partition if not using full drive LVM. Part of advantage of LVM is when it manages entire hard drive.
       
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

---

