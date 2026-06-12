---
title: "HOWTO: Create LiveUSBs from Windows using a GUI (uSbuntu Live Creator)"
date: 2009-01-06
forum: General Help
---

### Post by Slym.fr on 2009-01-06
Hi everybody,

I've made a software running in windows that creates a bootable and persistent USB stick with Ubuntu on it. It's called uSbuntu Live Creator.

You can download it here : [http://usbuntu.slym.fr]("http://usbuntu.slym.fr")

My software does almost the same thing as the USB Live Creator included in the 8.10 except it has more features.

It is working with Ubuntu, Kubuntu and Xubuntu and it allows you to run your USB key directly in windows without any software installation nor configuration, using a special portable version of VirtualBox.
It's really easy to use.

:popcorn: **_Creating an uSbuntu key is a five easy steps process :_** :popcorn:

[LIST]
[*]**step 1 :** launch the uSbuntu Live Creator and choose a USB key or drive in the list
[*]**step 2 :** select a ISO file or CD of Ubuntu/KubuntuXubuntu 8.10 Intrepid Ibex
[*]**step 3 :** choose the size of persistency data (usually more than 250MB)
[*]**step 4 :** check the options you want
[*]**step 5 :** click the thunder to start the creation
[/LIST]

Do not forget to use the customized helps (top-right end corner of each step).

Moreover, each needed step (1,2 and 3) has a traffic light to indicate its state. This is the interpretation :

[LIST]
[*]**Red light :** the step is not correctly fulfilled, you cannot start the creation
[*]**Orange light :** there is a non blocking problem on the step
[*]**Green light :** everything's fine
[/LIST]

Feel free to make any comments/suggestion/bug report but do not forget to check the help file before.

Hope you will enjoy it as much as i do.

Slym

This is a preview : 
[CENTER][IMG]http://usbuntu.slym.fr/img/usbuntu-preview-en.jpg[/IMG][/CENTER]

---

### Post by soldonz on 2009-01-10
Great software.

A minor problem with the language thoguh. the software automatically choose French as its language when I wanted it to be English. 

Is it possible to force its language to English?

---

### Post by dcstar on 2009-01-10
Gee, another one to add to the list:

[http://ubuntuforums.org/showthread.php?t=820887](http://ubuntuforums.org/showthread.php?t=820887)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by Slym.fr on 2009-02-15
dcstar> I should do that but i'm waiting a bit. I'm trying to improve it a bit before.

soldonz> you can force in english by modifying tools\settings\settings.ini and put "English" in force_lang.

---

### Post by FlowFlo on 2009-04-13
Hey,
thanks for sharing this great tool but there is one problem I can't handle.

I want to use a 64bit version of ubuntu 8.10 and when I choose the 64bit isofile the program says it is not compatible.

So I changed the name of the 64bit isofile to ubuntu-8.10-desktop-i386.iso and it started to check the file. But then an error appears which sayed that the file was right but corrupted.

My qustion now: Is it possible to use a 64bit version? (:

Thanks in advance

---

### Post by CDrewing on 2009-04-16
Really nice & makes fun. But how can I configure the virtual Ubuntu session like changing the screen size etc.? Even full screen runs as 640x480.

Second, I would like to give it a little bit more of RAM. On a 3 GB notebook I can give more RAM to it than the standard 256 MBytes.

Perhaps through a config file? Where is it located?

---

### Post by Tom Mann on 2009-04-28
I just come across usbuntu whilst browsing the internet, what a handy tool :KS

---

### Post by SteveMcGrane on 2009-08-23
Great Tool!

Just a tip:  I have a netbook with 1024x600 resolution.  When I move the program to better see step 5 (which is below the bottom of the screen) the program snaps back to the top of the screen.  A smaller skin or removing the snap to top of screen (maybe a windows "feature"?) would help.

---

