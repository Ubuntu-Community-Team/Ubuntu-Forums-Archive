---
title: "Boot Windows ISO off USB Drive"
date: 2009-02-02
forum: General Help
---

### Post by Thursday146 on 2009-02-02
After installing Ubuntu x64 my dvd drive keeps getting a device i/o error. I cant boot an install disk so im stuck in ubuntu. 

i do have a Windows Xp iso in my home folder and i was wondering if i extracted the iso to my usb drive (its a WD My Passport 320gb) and went into gparted and added a boot flag to the drive would it boot the windows install prompt??

---

### Post by Thursday146 on 2009-02-02
bump?

---

### Post by cariboo on 2009-02-02
The quick answer is no. I'm sure if you search some of the windows sites, you should be able to find a way to create a bootable usb thumbdrive.

Jim

---

### Post by BatteriesNotIncluded on 2009-02-02
Not sure how much it will help but have you looked into BartPE?

---

### Post by Thursday146 on 2009-02-02
> **BatteriesNotIncluded said:**
> Not sure how much it will help but have you looked into BartPE?

BartPE requires a dvd drive. 


> **cariboo907 said:**
> The quick answer is no. I'm sure if you search some of the windows sites, you should be able to find a way to create a bootable usb thumbdrive.

Jim

Dude i have been stuck in ubuntu for 4 days. For the last fackin 4 days i have been looking for a way out. 

trust me there is no website in this world we live in that talks about a usb bootable windows setup i have spent long long nights searching.

So please could someone with the actual knowledege direct me to what i need to do.

---

### Post by Thursday146 on 2009-02-02
EDIT: Every soultion i've found requires windows xp to already be installed to create a bootable usb. So ubuntu cant boot any operating system if it doesnt have a dvd/cd drive? that seems limiting to me.

my dvd drive worked on windows before i put ubuntu on and i spent $60 on it

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827131059](http://www.newegg.com/Product/Product.aspx?Item=N82E16827131059)

do i seriously have to buy a new dvd drive because i had to try out linux?

---

### Post by Thursday146 on 2009-02-02
???

---

### Post by MartyBuntu on 2009-02-02
Will your computer boot up with an Ubuntu installation CD?

---

### Post by Thursday146 on 2009-02-02
when i installed ubuntu x64. all windows dvds would not work. but my ubuntu x64 live cd still worked and my iaktos and kalway dvd worked. after all of the updates the dvd drive completely failed.

ubuntu doesnt recognize the dvd drive at all. keeps saying unable to mount. but my bios idenfies the dvd player and displays the model number

---

### Post by solitaire on 2009-02-02
Suggestion....

Install SUN xVM Virtual Box.
Create a virtual XP install using the ISO image.
start up the Virtual XP and use it to create a bootable USB drive with the instructions you found earlier.
Reboot with USB drive plugged in
Set BIOS to boot from USB device.
!!Win!! :D

---

### Post by Thursday146 on 2009-02-02
Wow props man i just installed virutalbox se right now. ill post the results

---

### Post by sztomi on 2009-02-26
[http://netbooks.modaco.com/content/msi/261632/installing-xp-via-a-usb-stick/](http://netbooks.modaco.com/content/msi/261632/installing-xp-via-a-usb-stick/)

Maybe...

---

