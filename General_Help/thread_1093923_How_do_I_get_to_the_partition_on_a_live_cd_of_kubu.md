---
title: "How do I get to the partition on a live cd of kubuntu 8.10"
date: 2009-03-12
forum: General Help
---

### Post by limiz on 2009-03-12
Yea I like to know. Can you help me out??

---

### Post by cantormath on 2009-03-12
> **limiz said:**
> Yea I like to know. Can you help me out??

if it is not mounted after the liveCD is booted, you need to mount the disk.  
In terminal, type

:~$ sudo fdisk -l

that should show you the partition tables and drives on the machine.

---

### Post by limiz on 2009-03-12
OK, this some what help me out. How can I delete them?

---

### Post by cantormath on 2009-03-12
> **limiz said:**
> OK, this some what help me out. How can I delete them?

You want to delete the partitions?
if so, open up terminal and start gparted.  Note: you will need to unmount the disk before you can make changes to it.  You can do this in Gparted.

---

### Post by limiz on 2009-03-12
I try to do start gparted. And it telling me that i need to be in root. I'm using a live cd. So how can I get into root using the live cd?

---

### Post by cantormath on 2009-03-12
> **limiz said:**
> I try to do start gparted. And it telling me that i need to be in root. I'm using a live cd. So how can I get into root using the live cd?

type
sudo gparted

it will ask for a password, and there is no password for the Livecd, just hit enter.

---

