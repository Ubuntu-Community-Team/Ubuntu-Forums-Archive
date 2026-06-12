---
title: "Ubuntu USB Live disc hangs part-way through setup. Please help!"
date: 2009-03-17
forum: General Help
---

### Post by Pipps on 2009-03-17
I have created a Ubuntu USB Live Disc using [these]("http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/") instructions. The setup was successful.

I rebooted my machine from USB, and selected the option to 'try Ubuntu'.

Mid-way through the Ubuntu Live boot process, I arrived at a black screen displaying with the following white text:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```
This is all that is displayed, with a blinking cursor for text input at the end. The Ubuntu start-up does not go any further than this point. Ubuntu does not ever load.

What has gone wrong with my USB Live disc? Please help!

---

### Post by Nano_ext3 on 2009-03-17
**Download the official disc from** 
[LIST][http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)[/LIST]

**Before burning, create an MD5 hash of the file:**

[LIST]
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[/LIST]

Use this after the disc is burnt to verify.  Burn at the slowest rate possible on your burner.  Compare the MD5 sums of your file to the disc.  You will find what you need in the community document above.

**If you are tyring to make a Live USB of Ubuntu**

[LIST]Download Unetbootin from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)[/LIST]

**Also , from 8.10 on, there is a EASY tool located under System > Administration > Make USB.  Note this is only on the LIVE DISC , and while you are booted into the life environment. This will AUTOMATICALLY make a USB jump drive for you!  If it doesnt let you, make sure to format the USB drive with gparted**

Hope this helps!

-Nano

---

### Post by ruel- on 2009-03-17
Try re-burning the disc, at a lower speed to make sure that the disc records all of its content..

happened to me in other linux distros, I have to re-burn due to excitement, I figured ou max speed isn't always the best option..

---

### Post by mazzaschi on 2009-03-17
I've got the same message currently from a disc that installed successfully on another computer. 

On a previous install of another ubuntu release I got that message due to the hard drive settings in my BIOS. I'm too much a newbie to help more specifically.

Good luck.

---

### Post by mazzaschi on 2009-03-17
FWIW, The info in this thread solved my problem:

 [ubuntu] initramfs + busybox trouble installing

---

### Post by bapoumba on 2009-03-20
13 posts have been removed. Yes, that was a heavy cleaning..
To the OP, please try to be considerate when people try to help you, thanks.
The thread has been brought to our attention and will be monitored, so please try to keep it civil. One more chance.

---

