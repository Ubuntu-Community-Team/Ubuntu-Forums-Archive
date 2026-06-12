---
title: "Virtual Box USB Problem"
date: 2009-03-24
forum: General Help
---

### Post by phr33k-dc on 2009-03-24
I have installed VirtualBox xVM on my system. 
I have an XP virtual system on it. 
I have gone onto the USB option and set a filter for my USB.
Its a SanDisk U3 Cruser Micro.
I cant see it in my virtual system. (cant use it)

Any ideas?

Thanks for any help.

---

### Post by phr33k-dc on 2009-03-24
Take a look at this.

---

### Post by phr33k-dc on 2009-03-24
it says unavailable for anything i put in as a usb

---

### Post by balloooza on 2009-03-24
That is because it is the opensource version (the one you get on the repository, the propriitory version is..

intrepid
[http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386.deb](http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386.deb)

or hardy
[http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb](http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb)

---

### Post by phr33k-dc on 2009-03-24
THanks for the response. I have version 2.1.4 is that the open source one?

---

### Post by balloooza on 2009-03-24
it might be, did you get it from using apt, synaptic, or the package manager, or from the virtualbox.org website

---

### Post by balloooza on 2009-03-24
read my befor post also, but have you tried insirting the usb devic, then unmounting it (or "safly remove") the usb stick, then see if you can mount it to windows.

The open source edition (OSE) might have added linux usb support yet.

---

### Post by phr33k-dc on 2009-03-24
I got it from the virtual box website. If you use synaptic it downloads VirtualBox OSE. But if you go to the website it downloads as VirtualBox xMV

---

### Post by phr33k-dc on 2009-03-24
that link you gave me is the link that i downloaded from oringinally. so i have that version

---

### Post by kyphi on 2009-03-24
xVM 2.1.4 is the current version from Sun Microsystems.

Before you can use a USB device, you have to "register" it in VBox in the USB section before you start the guest operating system.  You only have to do that once.

When you insert a USB device, Ubuntu automounts it and it is therefore not available to the guest system.  So, go back into Ubuntu and unmount the device - now it should be accessible by the guest.

Addendum:  Keep in mind that after doing all of the above you will have to wait for Windows (in VBox) to fiddle about with its "Found New Hardware Wizard".  This can take at least a minute.  But after that any USB device (printer, webcam, USB stick, etc) will be available when you open "My Computer" (if you have set it up that way).

---

### Post by spcwingo on 2009-03-24
I followed this guide to get my USB to work:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html]("http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html")

The useful part is about halfway down under "Prepare booting your VM".

---

