---
title: "Changing back ubuntu 8.10 to 8.04"
date: 2008-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by m_pourfathi on 2008-10-17
I have a Dell vostro 1510 laptop. I had ubuntu 8.04 installed on my windoes, I upgraded it to 8.10 beta last night. I just gives me lots of bugs! How can I change it back the way it was??

---

### Post by snowpine on 2008-10-17
The easiest is to re-install 8.04 and restore your /home from backup (you did back up before upgrading, right?)

---

### Post by m_pourfathi on 2008-10-17
No unfortunately not:(. I'm new to linux in fact and I didn't think of it. Is there any other way?

---

### Post by iponeverything on 2008-10-17
There is no reason why you can't backup your data now. If it was an upgrade not a clean install, all of your data is still there. Just pop in a usb stick and copy your home directory over to it.

BTW -- I don't think there is a way to back out of the upgrade. If you want 8.04 you going to have to do a reinstall.

---

### Post by jsonder on 2008-10-17
> **snowpine said:**
> The easiest is to re-install 8.04 and restore your /home from backup (you did back up before upgrading, right?)

This might be a good time to suggest a separate partition for the /home directory (where the user files are stored).

To illustrate I opened Gparted on my notebook:

[img]http://members.cox.net/so4plume/partitions.jpg[/img]

sda1 or "/" is the root directory where the operating system goes.

sda2 or "linux-swap" is the swap partiton (XP pagefile equivalent).

sda3 or "/home" is the partition on which the user files will be placed.

sda4 or "/media/disk" is a small partition on which Mint is installed (this is a dual-boot machine; mint is for movies I've bought and want to watch).

By having user files in a separate partition, you can chose to not format that partition while doing a "clean install" of an operating system.

I hope that this is clear and helps someone.

---

### Post by m_pourfathi on 2008-10-18
My main issue is my wireless adapter. I use a WLAN to connect to the internet. It was working properly before the upgrade. After the upgrade, the driver was installed properly I suppose, because ubutnu recognizes my WLAN device and also the Wireless networks that I can connect to. It just repeatedly asks for my network key, though I enter it correctly. My WLAN security type is WPA2.
My ethernet adapter works properly and I managed to connect through it to internet. What seems to be the problem?

---

