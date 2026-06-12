---
title: "How do I see my windows files?"
date: 2009-06-14
forum: General Help
---

### Post by marvlowe on 2009-06-14
I installed Ubuntu 9.04 while in Windows Vista using wubi. I guess this created a 17GB Ubuntu directory in windows on which the operating system was installed. Everything seems to work but I cannot see any directories using the file browser outside the ubuntu directory except for other partitions. Is there any way to access my picture and document files created in windows which are in the same partition as Ubuntu?

---

### Post by sailthesea on 2009-06-14
As I understand it wubi creates a virtual disc enviroment inside your windows drivespace which means you can't access files within the windows system because the whole disc is mounted but ubuntu is running within it {I think} A dual boot with a shared swap or home partition would be better then you can access files with both OS but this can be tricky 
 There may be a way to do what you want but I haven't found it:(

---

### Post by abn91c on 2009-06-14
windows files are in the **[COLOR="Blue"]/host[/COLOR]** folder

---

### Post by sailthesea on 2009-06-14
HOST!
 I never made the connection because I have nothing in there 
 My understanding of the way Wubi operates is wrong Obviously:oops:

---

### Post by Cuba71 on 2009-06-14
Instructions to mount UBUNTU “root.disk” from NTFS partition
sudo fdisk -l			- to find device

sudo mkdir /win		- make first directory and mount device
sudo mount /dev/sda2 /win

sudo mkdir /vdisk		- make second directory for root.disk and mount root.disk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

---

### Post by marvlowe on 2009-06-15
> **abn91c said:**
> windows files are in the **[COLOR="Blue"]/host[/COLOR]** folder

Thanks. That works

---

