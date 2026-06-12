---
title: "Format HDD to WBFS using linux"
date: 2013-11-24
forum: Gaming &amp; Leisure
---

### Post by arashiko28 on 2013-11-24
This is my very last resort!!! I have just bought a nintendo WII (now is when I can afford it, so spare the questioning). And bought a bundle of games (used) but I don't want to carry all this CDs up and down everywhere. I have a "cursed" drive, so burned backups won't work ever. I just finished backing up all the games I bought BUT I can't pass them to the hard drive because it's not wbfs formatted... I have tried the following:
1. Installing WBFS manager 3.1 for windows via WINE. (Installed, not loading, no message, no nothing!)
2. Installing WBFS manager 3.1 on windows 7 virtual box. (Won't read ANY USB)
2.a. Re-installed the guest additions on virtual box. Reboot. (NADA)
3. Installed QWBFS for Linux. Here I have two messages; "Can't open drive". And obviously "Can't format drive". I have tried both, formatting to FAT32 and NTFS. Though it does identify the drive.
4. Installed Wiithon. (Won't open.) used the command "sudo gpasswd -a $USER disk" User added, still nothing.
5. Installed Wii Backup Fusion. With this I have my ISO's files ready to be transferred, but no destination.
6. Downloaded wbfs_file and copied where it belong, the command does nothing.

Is there anything I'm doing wrong? I have followed every single tutorial in internet in English and Spanish, I even tried a German web page!!!

Reason to do this: I travel a lot, and would like to take the Wii with me. Without the bulk of CDs. And the obvious reasons of protecting the original CDs.

---

### Post by Zeroedout on 2013-11-25
My favourite tool to use is wbfs_gtk, when I'm too lazy to type. I have no idea if there is an Ubuntu package or not (as I use Arch). The original (and best) tools for WBFS are at [http://wit.wiimm.de/](http://wit.wiimm.de/) Those will work flawlessly, but it's all command line. The site is a little confusing but I learned to use it with the documentation there. I don't have time to write a tutorial now, reply if you can't figure it out and I'll respond when I can. 

I'm curious as to why WBFS when it's giving you such a problem? Most Wii iso loaders will load compressed images from a fat32 (vfat in linux) partition. You use standard Ubuntu tools like Gparted to format the drive. Then, instead of a compressed file system, you just compress each iso (and compressing the ISO should not need the program to even know about your Fat32 disk).

---

### Post by slooksterpsv on 2013-11-26
On VirtualBox did you install the extension pack (separate download on virtualbox.org website):

**VirtualBox 4.3.2 Oracle VM VirtualBox Extension Pack**  All supported platforms
Support for USB 2.0 devices, VirtualBox RDP and PXE boot for Intel cards. See this chapter from the User Manual for an introduction to this Extension Pack. The Extension Pack binaries are released under the VirtualBox Personal Use and Evaluation License (PUEL).

Try installing that as that will give you direct access to USB 2.0 devices. You may also need to add yourself to another group. Read the manual on there.

---

