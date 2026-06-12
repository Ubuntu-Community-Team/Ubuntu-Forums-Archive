---
title: "How do you install Andriod OS on Ubuntu"
date: 2015-01-31
forum: Desktop Environments
---

### Post by PopsTheSailor on 2015-01-31
It there an easy way yet to install the Andriod OS on Ubuntu? I use VirtualBox to run windows. Can I set up another virtual device with Android? I found a link that made you install Java JDK, android SDK then eclipse to run it. Is it possible yet to easily install it under Ubuntu somehow?

---

### Post by sammiev on 2015-01-31
I tried there ISO on a live USB which worked OK but never tried it under a VM yet or an install to a HDD.

I tried [this]("http://www.android-x86.org/download").

---

### Post by PopsTheSailor on 2015-01-31
So I don't have a lot of experience here. Are you saying to just install the ISO to a flash drive and then you can boot the laptop off the USB stick right into the Android OS?

---

### Post by sammiev on 2015-01-31
> **PopsTheSailor said:**
> So I don't have a lot of experience here. Are you saying to just install the ISO to a flash drive and then you can boot the laptop off the USB stick right into the Android OS?

You need to make a bootable USB or DVD using the ISO. You can use UNetbootin or mkusb or whatever program you used for making the bootable Ubuntu ISO you installed Ubuntu with.

I like [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") myself.

---

### Post by kerry_s on 2015-01-31
i think he's saying grab the latest iso & try it in virtual box.
[http://downloads.sourceforge.net/project/android-x86/Release%204.4/android-x86-4.4-RC2.iso?r=http%3A%2F%2Fwww.android-x86.org%2Fdownload&ts=1422733933&use_mirror=softlayer-dal](http://downloads.sourceforge.net/project/android-x86/Release%204.4/android-x86-4.4-RC2.iso?r=http%3A%2F%2Fwww.android-x86.org%2Fdownload&ts=1422733933&use_mirror=softlayer-dal)

ps: first thing you need to do is disable sleep/screenoff, whatever it's called. it needs to be set to never, once it sleeps theres no waking it up. thats for the live, don't know about installed. i had other issues so i didn't install.

---

### Post by grahammechanical on 2015-01-31
Android usually runs on ARM devices. So, we need an x86 version of Android. This link might help you.

[http://www.howtogeek.com/164570/how-to-install-android-in-virtualbox/](http://www.howtogeek.com/164570/how-to-install-android-in-virtualbox/)

[https://code.google.com/p/android-x86/downloads/list](https://code.google.com/p/android-x86/downloads/list)

I might give this a try myself. Please use this thread to keep us informed if this is successful.

Regards.

---

### Post by sammiev on 2015-01-31
> **grahammechanical said:**
> Android usually runs on ARM devices. So, we need an x86 version of Android. This link might help you.

[http://www.howtogeek.com/164570/how-to-install-android-in-virtualbox/](http://www.howtogeek.com/164570/how-to-install-android-in-virtualbox/)

[https://code.google.com/p/android-x86/downloads/list](https://code.google.com/p/android-x86/downloads/list)

I might give this a try myself. Please use this thread to keep us informed if this is successful.

Regards.

Thanks for the updated link, I see it contains newer ISO's than the one I posted.

I will try it again myself.

---

### Post by grahammechanical on 2015-01-31
I tried the ISO image from the two links that I provided and I did not get very far. The live session loads up to "Detecting Android-86" and presents a progress bar of dots being printed to the screen does not get farther than that on my machine. There is also a VESA mode which I tried with the same results. Ctrl+Alt+Del does restart the machine without any ill effects.

This link might be more useful. I have downloaded Android-x86-4.4-Rc2.iso and am about to try it out.

[http://www.android-x86.org/](http://www.android-x86.org/)

[http://www.android-x86.org/download](http://www.android-x86.org/download)

Regards.

---

### Post by kerry_s on 2015-01-31
> **grahammechanical said:**
> I tried the ISO image from the two links that I provided and I did not get very far. The live session loads up to "Detecting Android-86" and presents a progress bar of dots being printed to the screen does not get farther than that on my machine. There is also a VESA mode which I tried with the same results. Ctrl+Alt+Del does restart the machine without any ill effects.

This link might be more useful. I have downloaded Android-x86-4.4-Rc2.iso and am about to try it out.

[http://www.android-x86.org/](http://www.android-x86.org/)

[http://www.android-x86.org/download](http://www.android-x86.org/download)

Regards.

i put the link straight to the iso.
[http://downloads.sourceforge.net/project/android-x86/Release%204.4/android-x86-4.4-RC2.iso?r=http%3A%2F%2Fwww.android-x86.org%2Fdownload&ts=1422733933&use_mirror=softlayer-dal](http://downloads.sourceforge.net/project/android-x86/Release%204.4/android-x86-4.4-RC2.iso?r=http%3A%2F%2Fwww.android-x86.org%2Fdownload&ts=1422733933&use_mirror=softlayer-dal)

save you time clicking around

---

### Post by grahammechanical on 2015-01-31
I have just tried the Android-x86-4.4-RC2 ISO image and I get no further than Detecting Android-x86. I allowed it more than 30 minutes before giving it the 3 finger salute.

I may try the install session tomorrow. Or the debug session. See if that is more useful.

Regards.

---

### Post by sammiev on 2015-01-31
I tried it live and it works great. ( picked up all my hardware as well ) Will install it into VMware later tonight and post back.

---

### Post by kerry_s on 2015-01-31
> **sammiev said:**
> I tried it live and it works great. ( picked up all my hardware as well ) Will install it into VMware later tonight and post back.

let me know how that go's. the main issue i had when running live was app's crashing or just didn't work, so i chose not to install, didn't want to take the chance of installing only to find i can't use the app's i want to use. i don't think hardware rendering was on for me.

---

### Post by grahammechanical on 2015-01-31
I found these documentation links about adding nomodeset (which I think that I will need) and what happens during install process. The information is a bit old. I note to use an Ext3 partition and not to install Grub because it will only detect Android-x86. The documentation speaks of grub menu.list. So, it is old. I will experiment. I have 2 HDD with different installs of Ubuntu on. So, I will not lose access to an install of Ubuntu.

[http://www.android-x86.org/documents/installhowto](http://www.android-x86.org/documents/installhowto)

[http://www.android-x86.org/documents/how-to-boot-the-android-x86-live-cd-when-you-have-problems-with-your-graphiccard](http://www.android-x86.org/documents/how-to-boot-the-android-x86-live-cd-when-you-have-problems-with-your-graphiccard)

[http://www.android-x86.org/documents](http://www.android-x86.org/documents)

@sammiev

I am glad someone has had success.

Regards.

---

### Post by sammiev on 2015-01-31
Installed well into VMware but ran like crap. Programs installed like firefox but would crash when loaded. Updates went well but mouse was jerky, will try a live install to the HDD and see how that works.

---

### Post by sammiev on 2015-02-01
Installed to my spare HDD and it ran great. Used it for the evening and enjoyed the run. Look forward to the next release, this release was a little older than the one that's on my tablet.

---

### Post by kerry_s on 2015-02-01
> **sammiev said:**
> Installed to my spare HDD and it ran great. Used it for the evening and enjoyed the run. Look forward to the next release, this release was a little older than the one that's on my tablet.

no more issues with crashing?

---

### Post by sammiev on 2015-02-01
> **kerry_s said:**
> no more issues with crashing?

On the VM it was not pretty.

---

### Post by kagashe on 2015-09-28
This is an old thread but never mind.

I initially tried the official latest stable version android-x86-4.4-r3 live which could boot into root terminal (no GUI). I posted on Google Groups and was told that my card AMD E1-6010 APU with AMD Radeon R2 Graphics.was supported on Lollipop Test Build.

These builds were ISO images with EFI Folder but did not boot on EFI, so I switched to Legacy on BIOS and I could boot to GUI. I also tried one latest test build which had Google Play. It works but sometimes reboots due to bugs.

In the process I learned how to boot the live usb disk and installed one on grub2 EFI without changing BIOS to Legacy which may be useful information here.
My /etc/grub.d/40_custom has following menu entries:
```
menuentry 'Android-x86 5.1 live' --class android-x86 {
	set root='(hd1,msdos1)'
	linux /kernel root=/dev/ram0 androidboot.hardware=android_x86 quiet SRC= DATA=
	initrd /initrd.img
}

menuentry 'Android-x86 5.1 on sda13' --class android-x86 {
	set root='(hd0,gpt13)'
	linux /android-2015-08-16/kernel root=/dev/ram0 androidboot.hardware=android_x86 quiet SRC=/android-2015-08-16 DATA=/android-2015-08-16/data
	initrd /android-2015-08-16/initrd.img
}

```
The first entry is to boot live on sdb1, the second one is to boot installed one on sda13. Android Lollipop install requires ext4 partition to work properly.

Kamalakar

---

