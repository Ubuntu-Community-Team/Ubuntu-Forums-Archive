---
title: "Help! Partitions..."
date: 2005-01-16
forum: Desktop Environments
---

### Post by pgoya on 2005-01-16
Hello to all.

What program I may use to partition my hd?? I want to resize the Windows Partition and left more space to Ubuntu.
What's the name of the partitioning program that Ubuntu uses at installation??

Thanks!

---

### Post by Adrenal on 2005-01-16
Not sure about what Ubuntu uses, but try QTParted

---

### Post by feneks on 2005-01-16
I think Ubuntu uses some kind of fdisk at installation. But this isn't suitable for your needs. To do resizing I recomend PartitionMagic. It's a comercial, proprietary program for Windows. There exists a posibility to do resizing with Linux but this isn't mature jet.
To be honest, I don't know the very actual situation.

--edit--
No matter what you do don't forget to do backups before!

---

### Post by feneks on 2005-01-16
[QUOTE=Adrenal]Not sure about what Ubuntu uses, but try QTParted[/QUOTE]

And **parted** for the terminal-priests.  :wink:

---

### Post by Xian on 2005-01-16
Ubuntu uses parted during the installation. I would recommend using QTparted, which is just the GUI version to do your partitioning. If you use a win-com proggy, you run the risk of a future Linux installation having difficulty with HD geometry issues caused by those win-x applications.

---

### Post by JackDog on 2005-01-17
qtparted (and parted) has a great interface, however I have had it destroy existing paritions before. I am not trying to flame them, its just happened too many times over the years. I usually just use fdisk from the command line. Its simple and easy to use. Checkout the gentoo install page for a quick howto. You will know all that you need to know in 5 minutes.

---

### Post by pgoya on 2005-01-17
[QUOTE=Xian]Ubuntu uses parted during the installation. I would recommend using QTparted, which is just the GUI version to do your partitioning. If you use a win-com proggy, you run the risk of a future Linux installation having difficulty with HD geometry issues caused by those win-x applications.[/QUOTE]
 Thanks!! It looks perfect to me. Installing....

---

### Post by akurashy on 2005-01-17
i did mine manually using ubuntu 
i just need to install windows and edit grub i think

---

