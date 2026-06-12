---
title: "automount (volume manager)"
date: 2005-06-29
forum: Desktop Environments
---

### Post by wdso on 2005-06-29
Hi,

I'm using Kubuntu 5.04 with KDE 3.4.1. Automounting (e.g USB key drive) doesn't work reliably. Sometimes, I can just plug in my stick and after a couple of seconds an icon shows up, clicking on it mounts the device. Most of the time though, nothing happens. tailing messages indicates, that udev created an entry in /dev, however, KDE does not show up an icon.

Whats so strange about this problem is its randomness. Sometimes, when automounting stops working, even rebooting the machine doesn't help. I wonder if there are any stale files lying around? Whats the correct procedure to get automounting working again?

Thanks!

---

### Post by caspar_wrede on 2005-06-29
Sorry, I can't help you and it works for me, but I have a related question:

How to you mount for example a USB stick via the shell. If I insert it and click on the resulting desktop icon it gets mounted on /media/sda1, but typing mount /media/sda1 doesn't work. What should I enter instead?

---

### Post by wdso on 2005-06-29
Actually, udev should create an entry in the fstab file as soon as you plug in the device, so mount /mountpath should work when you know the mountpath. 
You can try to monitor messages via tail -f /var/log/messages, you can than extract the name of the device (e.g. /dev/sda) and then mount it directly (e.g. mount /dev/sda1 /mnt/usb-stick.

---

### Post by Terracotta on 2005-07-10
It gets mounted to media:/sda1 not to /media/sda1. It actually gets mounted to /mnt/sda1, but to make it simple they  (I think) created something like file:/.... or [http://.](http://.)...
Oh maybe it could be media://sda1 (but I'm not on my kubuntu working right now so I can't tell, it's either one of those to).

---

### Post by Niber on 2005-08-01
[QUOTE=caspar_wrede]Sorry, I can't help you and it works for me, but I have a related question:

How to you mount for example a USB stick via the shell. If I insert it and click on the resulting desktop icon it gets mounted on /media/sda1, but typing mount /media/sda1 doesn't work. What should I enter instead?[/QUOTE]
 To mount the removable devices you should type pmount /dev/sda1 (sda2, etc) and punmount after having done the desired tasks. This is my temporary solution to the problems regarding randomness in automounting and I am seeking for the real one too.

---

### Post by !nkubus on 2005-08-01
Mine does not work at all right no HAL integration , it seems completly  screwed at the moment  even with digital camera. 

Anyone have this problem?

It was working last week ... :?  :? 

thanks

---

### Post by Firetech on 2005-08-02
[QUOTE=Terracotta]It gets mounted to media:/sda1 not to /media/sda1. It actually gets mounted to /mnt/sda1, /../.[/QUOTE]
Wrong, it gets mounted to /media/[whatever]. Atleast for me, both in Gnome and KDE. I guess the media:/ is to simulate "My Computer" in Windows.

One way of fixing automount without any need for user commands is to use gnome-volume-manager (YES, even in kubuntu. Some KDE distro's use it by default, there's no need for KDE to reinvent one of gnome's weels...)
If you don't have gnome (ubuntu) installed, install the package gnome-volume-manager with synaptic/kynaptic/apt-get/etc...
Press alt+f2 and type "gnome-volume-properties" (without the quotes) to control the settings for it. Then start the magic by pressing alt+f2 and typing "gnome-volume-manager" (again, without the quotes).

You might want to add it to KDE autostart too... Typing "ln -s /usr/bin/gnome-volume-manager ~/.kde/Autostart/gnome-volume-manager" (yet again, without the quotes) in the alt+f2 dialog should work.

However, the correct way to mount and unmount removable drives manually in kubuntu is pmount /dev/[whatever] (mount) and pumount /dev/[whatever] (unmount).

---

### Post by echinida on 2005-08-08
I have the same problem USB stick mounts OK as media:/sdb1 and I can open files etc but no icon appears, tried reinstalling HAL as mentioned in one post and also installing gnome-volume-manager. CD's behave similarly, also no trash bin. All of this is OK when booted from the live CD. Oh and I updated KDE to 3.4.2 just incase that fixed it, but no.
What files should I compare between the live CD install and this one? Any other suggestions?

---

