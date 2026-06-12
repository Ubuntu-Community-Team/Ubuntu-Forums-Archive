---
title: "Ok im back"
date: 2009-04-07
forum: General Help
---

### Post by Ryoukii on 2009-04-07
Hi. A while ago i got a live cd shipped over to me and i tryed to try it out with no sucess i kept getting hazzy lines on the screen and it wouldnt boot. Evryone said it was because of my graphic card ATI RADEON x600. Well recently ive been using Debian in Vmware player and booting up Slax on a usb. Anyways today i said i would try ubuntu in vmware player by making a iso file from my cd. Ubuntu worked perfect in VMware player no graphic issues or nothing. Now what i want to know is does this mean that ubuntu is capable of running on my computer with my graphic card since it worked on vmware player ? Also what do you think is better and faster ? A Bootable USB Ubuntu or Install ubuntu using wubi from the Cd ?. I dont want to install using Wubi then find out it wont work. Btw i dont want to partition my HD.

Hope someone can help ?

---

### Post by cariboo on 2009-04-07
Installing to the hard drive is always going to be faster then running from a usb device. 

Jim

---

### Post by anjilslaire on 2009-04-07
Boot the live cd on your system and see if everything works. IT'll run a bit slow, but you'll know  what works and what doesn't.

---

### Post by Mimoo_Tz on 2009-04-07
Installing to the hard drive is always going to be faster then running from a usb device.

these is sure , because Flash disk is a statitque structure , ... I don t know how can I explain it , ... but the big defférent is in the structure construction , ......Diodes , transt , ...

---

### Post by Ryoukii on 2009-04-07
> Boot the live cd on your system and see if everything works. IT'll run a bit slow, but you'll know what works and what doesn't.

The live cd i got shipped over wouldnt let me try out ubuntu i kept getting hazzy lines on the screen and people told me this was because of my graphic card. But the .iso image from the live cd works in vmware. should i burn a new livecd maybe and try it out ?

---

### Post by Peasantoid on 2009-04-07
> **Ryoukii said:**
> should i burn a new livecd maybe and try it out ?
Worth a try.

---

### Post by albinootje on 2009-04-07
> **Ryoukii said:**
> Ubuntu worked perfect in VMware player no graphic issues or nothing. Now what i want to know is does this mean that ubuntu is capable of running on my computer with my graphic card since it worked on vmware player ? 
All emulation/virtualisation software like VirtualBox, Qemu, VMware use virtual vide-cards.
The fact that Ubuntu works fine in VirtualBox doesn't mean it will be running fine now when installed to your hard disk.

Just burn the Jaunty Beta Desktop cdrom, or use "unetbootin" to put it on an usb-stick (larger than 1 Gb), and use the live session ("try without installing") to check the results.

---

### Post by Ryoukii on 2009-04-07
I dont know what you mean by jaunty beta desktop. how about i just make a another livecd and try it out then il know if my graphic card is able to run ubuntu ?

---

### Post by anjilslaire on 2009-04-07
you probably need to boot it in safe graphics mode, there should be an option to boot from that after the intial bootup where you select what you want to do with the disc.

---

### Post by albinootje on 2009-04-08
> **Ryoukii said:**
> I dont know what you mean by jaunty beta desktop. how about i just make a another livecd and try it out then il know if my graphic card is able to run ubuntu ?

Here are the iso images I referred to :
[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

---

