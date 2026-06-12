---
title: "First Time with ubuntu"
date: 2009-04-03
forum: General Help
---

### Post by hojnikb on 2009-04-03
I have a few noobish questions about ubuntu.As you will see i'm a complete begginer in linux world.Becouse i wanted to try ubuntu i've installed it on my 8gb usb-stick not to mess up with my Windows installation.Now theese are the questions:
-How can i set the bootloader to boot directly from usb stick without welcome screen (eg select language and then start ubunu without harm ...)
-how do i get rid of the Install shortcut on my desktop becouse every time i boot up to desktop  it shows again (even if i delete it)
-how can i set the nvidia driver to load each time when i'm on pc with nvidia card (i hate to load driver each time and then relogin my season)
-is it possible to run xmms  on ubuntu ?
-every time when i boot up clock sets back to gmt 0 (i have set it to my default gmt 1+/2+ it just overrrides my settings)and where can i set custom ntp severs

any help would be really appreciated.

---

### Post by taurus on 2009-04-03
Sounds to me like you actually didn't install Ubuntu on your USB thumbdrive.  Instead, you use it as a LiveCD.

---

### Post by aeiah on 2009-04-03
how did you install it to your usb drive? because it sounds like you either have an ubuntu live usb, or you've kept the livecd in the drive. doesnt seem like you installed ubuntu at all and if you did, it probably isnt what you're looking at.

---

### Post by hojnikb on 2009-04-03
Actually i've used "Make USB Stratup Disk" set to save all settings into capser-rw.

---

### Post by Kareeser on 2009-04-03
Right. That essentially turns your USB key into a Live CD. You still need to install Ubuntu onto your computer.

---

### Post by hojnikb on 2009-04-04
soo that means i can't fix this.

---

### Post by LoloftheRings on 2009-04-04
```

sudo apt-get install xmms2

```

should install xmms.

For the booting issue, you may be able to change boot priority in your BIOS. Set the first option to removable media or usb drives.
Second is often CD/DVD and the third hard drive.

I'm not sure about your other problems though.

Good luck

---

### Post by ShaunG on 2009-04-04
You can install ubuntu onto your 8gb usb drive if you wish. 

First off format your usb stick. 

Stick the live cd in your pc and reboot, stick in the blank usb key too.

Now choose Install Ubuntu.

When it comes to the "Prepare Disk Space" Screen select Manual.

Select your usb key .. IT IS VERY IMPORTANT YOU SELECT YOUR USB KEY.

Also at the bootloader screen, click advanced and make sure you install the bootloader on your usb.

If you do the above steps wrong you will format other data on your pc!!!!

Then follow the rest of the steps as normal.

This should work, I have not tried it. (Will now though)

But please be careful, I don not wish to see you install in the wrong partition.

---

### Post by soomro on 2009-04-04
i want to install kubuntu in 1gb usb :lolflag:

---

### Post by ShaunG on 2009-04-04
I tried it and it appears to have worked. 

Although you may need to mess with your bios setup specifically in the boot section to get the pc to boot from the usb.

Also installing kubuntu on a 1gb stick for what? As a live usb or as an actual usable portable os? Because 1gb isn't much for the latter

---

