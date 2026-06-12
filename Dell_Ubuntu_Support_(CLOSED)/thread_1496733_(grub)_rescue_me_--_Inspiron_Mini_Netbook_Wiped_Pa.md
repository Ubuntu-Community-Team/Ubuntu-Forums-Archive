---
title: "(grub) rescue me -- Inspiron Mini Netbook Wiped Partition"
date: 2010-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ajc0118 on 2010-05-29
After downloading Ubuntu 10.04 and wiping windows off my brand new Inspiron Mini netbook, I was playing around in the hard disk manager trying to clean up the the extra partitions I had accidently created during the install (all of which were partially completed ubuntu partitions, my power died during one install and i didnt install the desktop function to the other)--

Looking at the 4 partitions on the disk, I guessed at which one was the shell OS I had installed earlier and told linux to delete it- i guess wrong, and shortly into the process ubuntu told me some of the files i was trying to access were read only and it needed to reboot to determine if the OS was still stable.  Since then, the netbook has been dead.

Powering on from shutdown, it shows the Dell logo with the bar at the bottom, and the options for setup and boot options- when the bar loads, a shell comes up that says -
"GRUB loading.
error: no such partition
grub rescue>"  

It seems like the netbook will not take external input.  I tried reinserting the flash drive I had installed the OS off of, even rolling back to a previous version of Ubuntu 9, but it seems like the USB ports will not forward any data to the machine.  

A repair guy I brought to look at it told me I cant remove the HD from this machine, that Inspirons weren't build that way.  His suggestion was to load an external CD or Floppy drive with an 'Fdisk reformat' program on it.  I have no data I need saving on this machine, its essentially brand new, so my only priority is wiping whats on it clean and getting it back to factory status so I can load Ubuntu clean. 

I've read the boards, I can't find any thread that relates to my case- since the HD can't be removed my only recourse seems to be plugging an external floppy or cd drive with Ubuntu 10.04 grub-rescue software.  

I'm a Ubuntu neophyte; this represents my first of assuredly many complete screw-ups of my machine before I get the OS down pat- any advice on what to do would be just thrilling.  Please help me out, guys.  :)

---

### Post by bcbc on 2010-05-29
> **Ajc0118 said:**
> it seems like the USB ports will not forward any data to the machine.  


So when it boots, you hit F12 for boot options, and select "boot from usb", and nothing happens?

If you can boot a live usb, then maybe testdisk can recover your data or just reinstall.

---

### Post by ugm6hr on 2010-05-29
> **Ajc0118 said:**
> Powering on from shutdown, it shows the Dell logo with the bar at the bottom, and the options for setup and boot options- 

Press the button for Boot Options (? Delete or Escape) at this stage, and then boot from a Live USB.

This should work, since the BIOS boot options come before the SSD card boots (with a Grub error).  If this also gives a Grub error, then there may be a problem with your Live USB.

---

