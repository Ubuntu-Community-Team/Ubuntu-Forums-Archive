---
title: "How to format usb"
date: 2009-04-22
forum: General Help
---

### Post by frozenfire0808 on 2009-04-22
How do you format a flash drive to FAT32? I'm using a 1 Gig that i dont care about before I try to format a 500 gig external hard drive to FAT32 so my Playstation 3 will recognize it

---

### Post by James_Lochhead on 2009-04-22
Use a program called GParted. It is in Add/Remove programs or Synaptic.

First make sure you have the right device selected (top right). Delete all partitions on it, create a fat32 partition, then apply changes.

---

### Post by frozenfire0808 on 2009-04-22
where does gparted show up at? I have already searched applications and system tools

---

### Post by PaulReaver on 2009-04-22
Gparted is the standard partition software in the ubuntu installer.
If you installed ubuntu you already installed gparted.  
Just type "sudo gparted" in a terminal. 
But be carefull gparted is a weapon of mass destruction.
It could wipe your hdd partitions.

---

### Post by frozenfire0808 on 2009-04-22
thanks gparted showed up after using   sudo gparted

---

