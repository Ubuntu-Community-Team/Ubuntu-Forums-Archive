---
title: "Trying to boot moblin with ubuntu"
date: 2009-06-10
forum: General Help
---

### Post by cody7002002 on 2009-06-10
So i downloaded moblin burned the image to my flash drive like the instructions on the moblin site said to. Then I went into my computers setup to make sure the usb drive was first in boot priority. I made it that but still when I turn the computer on it always boots into ubuntu. What can I do to get moblin to run?

---

### Post by ddrichardson on 2009-06-10
Well, I've no idea what you're trying to run it on but there usually an option from BIOS to select the boot media - it's F12 on an aspire one.

---

### Post by cody7002002 on 2009-06-10
Im using an asus eeepc 1000he

---

### Post by ddrichardson on 2009-06-10
Some flash drives won't play when it comes to booting, I have no idea why - Bytestor are particularly bad for it.

According to Google, pressing F2 on boot on a 1000he gets the boot menu.

---

### Post by cody7002002 on 2009-06-10
Yeah I did that I got to the boot menu and made sure the flash drive had top priority. I'm going to try using another flash drive...

---

### Post by ddrichardson on 2009-06-10
FWIW I wouldn't install it thinking it'll be faster because it isn't - runs the same off of USB.  If you do then you'll be better checking the manual partitioning option because it defaults to ext3, journaled FS and SSD (if you have solid state) don't mix well.

---

### Post by cody7002002 on 2009-06-10
I'm only trying it out because I want to see what it's like. I've heard many people talking about it and I want to try it for myself.

Ok I've tried two separate flash drives two times each and neither of them have worked X(

---

### Post by ddrichardson on 2009-06-10
It runs in VirtualBox quite well and the front end (my_zone I think its called) is good, if you twitter a lot.

---

### Post by cody7002002 on 2009-06-10
ahh this is driving me crazy. I don't know why it won't boot i've booted ubuntu from this drive before so i know it is bootable...

---

### Post by ddrichardson on 2009-06-11
> **cody7002002 said:**
> ahh this is driving me crazy. I don't know why it won't boot i've booted ubuntu from this drive before so i know it is bootable...
When did you get the image? Which instructions did you follow.

---

### Post by Fatman_UK on 2009-06-11
Did you unmount the flash drive before putting the image onto it? If you don't do that, Ubuntu can interfere with the copy somehow, according to moblin.org.

The command will be something like:

sudo umount /media/disk

Look in the /media dir to find out what the mount point is.

Good luck!

---

### Post by ddrichardson on 2009-06-12
I just used usb-imagewriter from the repositories to write the image:
```
sudo apt-get install usb-imagewriter
```
It'll install under Applications->Accessories->USB ImageWriter and its very straightforward.

---

### Post by Flash858 on 2009-06-15
You hit the ESC key when the machine is booting. It will bring up a boot device selector, and you can select your USB drive. I have found it does not work however, and I had to put the installer on a SHDC card, and it booted from there just fine.

---

