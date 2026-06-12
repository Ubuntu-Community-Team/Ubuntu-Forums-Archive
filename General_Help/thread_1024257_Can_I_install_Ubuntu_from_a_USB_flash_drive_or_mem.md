---
title: "Can I install Ubuntu from a USB flash drive or memory stick?"
date: 2008-12-28
forum: General Help
---

### Post by Moonfrost on 2008-12-28
Well I know you can install certain Linux distros from USB pen drives. But can I install from a memory stick (providing my BIOS allows me to boot from it)? are there special files (like a special Ubuntu or other linux distro "version" for USB flash drives or memory sticks or whatever) I need to download? or could I just use the conventional ISO? I've been thinking on trying to install Ubuntu on another hard drive and I ran out of DVDs (it's ultimate edition that's why I need a DVD) and I have a few MicroSD 2gb cards laying around a 4gb Memory Stick Pro Duo (for my PSP, but it's brand new and I have nothing on it yet) and was thinking if I could install from that?

The Image file is 1.7gb...I highly doubt I could do it from an ISO but I really never heard how you install from USB pen drives or memory sticks at all so I wanted to know how to specifically do it that way (of course as I said, providing my BIOS can boot from such a device).

---

### Post by fooman on 2008-12-28
if you are using intrepid 8.10...go to system > administration > create a usb startup disk

if you do not have 8.10 installed...see here:

[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

---

### Post by Moonfrost on 2008-12-28
> **fooman said:**
> if you are using intrepid 8.10...go to system > administration > create a usb startup disk

if you do not have 8.10 installed...see here:

[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

I'm using 8.10, but I have KDE (Kubuntu), how would I do that from here? I have read a guide but I wasn't done yet when you already replied!

---

### Post by zeronothing on 2008-12-28
if you have a ubuntu 8.10 installation on another computer somewhere you can use the new feature "Create USB Startup disk." it is located under System -> Administration -> Create a USB startup disk.

this is one way I know of where you can install ubuntu on a usb stick. Then use it to install ubuntu on PCs using the USB stick. In essences the USB stick is now a live cd but only in USB form.

---

### Post by fooman on 2008-12-28
> **Moonfrost said:**
> I'm using 8.10, but I have KDE (Kubuntu), how would I do that from here? I have read a guide but I wasn't done yet when you already replied!

in kde...go to applications > system > create a usb startup disk

---

### Post by MartyBuntu on 2008-12-28
> **zeronothing said:**
> if you have a ubuntu 8.10 installation on another computer somewhere you can use the new feature "Create USB Startup disk." it is located under System -> Administration -> Create a USB startup disk.

this is one way I know of where you can install ubuntu on a usb stick. Then use it to install ubuntu on PCs using the USB stick. In essences the USB stick is now a live cd but only in USB form.

That's exactly how I installed Ubuntu 8.10 on my daughter's Dell Inspiron laptop with a broken DVD drive. Works great.

---

### Post by Moonfrost on 2008-12-28
> **fooman said:**
> in kde...go to applications > system > create a usb startup disk

I can't find that in KDE, by the way I need to format it using FAT32, will the "create a usb startup disk" do that for me? can I set it up like that? or does it automatically create a USB startup disk provided you only use official Ubuntu? my Ubuntu Ultimate Edition image is 1.7gb so I need FAT32.

---

### Post by skippymo on 2008-12-28
if you use windows you can make one with pe to usb just download the ubuntu 8.10 .iso and save it, download pe to usb from [http://gocoding.com/page.php?al=petousb](http://gocoding.com/page.php?al=petousb) and use it to make the bootable usb drive. if you cant get ubuntu or kubuntu to work right...just another option for you, also great for other things that you want to make a bootable drive...hope that helps too.

---

### Post by Moonfrost on 2008-12-28
> **skippymo said:**
> if you use windows you can make one with pe to usb just download the ubuntu 8.10 .iso and save it, download pe to usb from [http://gocoding.com/page.php?al=petousb](http://gocoding.com/page.php?al=petousb) and use it to make the bootable usb drive. if you cant get ubuntu or kubuntu to work right...just another option for you, also great for other things that you want to make a bootable drive...hope that helps too.

I'll try that since I have Windows on another partition, thanks.

EDIT: Nevermind, it turns out I found on a website I had to download usb creator, so I just went to adept and installed it, we'll see how it comes out...

---

### Post by skippymo on 2008-12-28
let me know if you need help with it, it is really simple tho....good luck....i'm a windows admin and i use ubuntu more than xp but whatever works....

---

### Post by fooman on 2008-12-28
> **Moonfrost said:**
> I can't find that in KDE, 

install the usb-creator package...in a terminal:

```
sudo apt-get install usb-creator
```

---

### Post by Moonfrost on 2008-12-29
> **fooman said:**
> install the usb-creator package...in a terminal:

```
sudo apt-get install usb-creator
```

Yeah thanks, I was able to find it on the repos and I successfully installed from a MicroSD card using the USB MicroSD reader for the first time ever! the Live environment runs really fast when running from the card!

---

### Post by Moonfrost on 2008-12-29
Thanks guys for all your help!

---

