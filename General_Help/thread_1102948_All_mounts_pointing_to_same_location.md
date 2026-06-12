---
title: "All mounts pointing to same location?"
date: 2009-03-22
forum: General Help
---

### Post by hm.in.vegas on 2009-03-22
Apologies if this has been dealt with before. I am a newbie and apparently I couldn't find the correct search terms.

I have installed Linux in a dual-boot system with Vista and the following configuration

sda (Windows OS, Linux OS, SWAP and a windows partition i want to be able to access and share)
sdb
sdc

On bootup the system mounts all three drives and labels them with the Drive Labels I setup in Windows. In my case Drive 1 (sda), Drive 2 (sdb), Drive 3 (sdc). Good so far.

The problem is that no matter which of these drives I try to access, only the contents of Drive 2 are displayed in the finder. Seems like all the mounts are somehow pointing to the same location. 

The problem is I don't really know where to start looking for the root of the problem. Any ideas?

Thanks in advance. Any help would be greatly appreciated.

---

### Post by Jimmyfj on 2009-03-22
Seems to me you need to install SAMBA and NTFS Configuration Tools in order to obtain a Win-share on the 3'rd

Open a terminal and type in this command:

```
sudo apt-get install samba
``` 

From your programs menu go to Add/Remove at the buttom and either from there, or from System>Administration>Synaptic install the NTFS Configuration Tools program.

---

### Post by Arthur73 on 2009-03-22
I am just considering a dual boot configuration on a laptop. I had expected to setup a fat32 formatted partition to jointly share files that could be read by Win & Ubuntu. In your case it may mean adding a partition, sized to the volume of file storage that seems suited to your shared files.

There may be other approaches and I will monitor for newer details.

Arthur

---

### Post by Arthur73 on 2009-03-22
Additional guidance may be found here.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Arthur

---

