---
title: "Ubuntu 9.10 Dell Mini 9 Installation"
date: 2009-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mikazukinoyaiba on 2009-12-03
I recently purchased a 32GB SSD from Supertalent and installed it into my Dell Mini 9.

Using Unetbootin I created a bootable USB stick of the 9.10 release and tried to install the operating system onto my hard drive, but with trouble.

During installation, while partitioning the drive, I received an error notice about ext4, I told the installation to continue and now it is stuck at 70% while "detecting file systems".

If I turn off the system and try reinstalling the OS, it jumps straight to the 70%, remaining there without any signs of progress.

Is this a common error? Is there something wrong with my harddrive?

Keep in mind I'm using the netbook remix iso file.

---

### Post by Mikazukinoyaiba on 2009-12-03
Still need help, this is the error I receive:

Creating ext4 file system for / in partition #1 SCSI1 (0,1,0) (sda)

The attempt to mount a file system with type ext4 in SCSI1 (0,1,0) partition #1 (sda) at / failed.

I received a similar error when I tried using file type ext3.

---

### Post by ugm6hr on 2009-12-05
Sounds like a hardware problem.

If you just run the LiveUSB, are you able to format and mount the internal SSD?

---

