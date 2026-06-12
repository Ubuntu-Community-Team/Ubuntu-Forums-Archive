---
title: "ubuntu-minimal was broken"
date: 2009-06-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by murap on 2009-06-28
Hi
I'm using Dell mini9 (Ubuntu 8.04 pre-installed).

I have a problem that "ubuntu-minimal" was broken, so I cannot install anything now.
For some reasons, I cannot connect to the internet by this PC, so it is impossible to use synaptic package manager to recover "ubuntu-minimal".
Is there any good way to fix this without connecting to the internet?

I wrote the situation under which I'm suffering now below.


After I just bought Dell mini9 and when I followed the update manager to download updates,
I came not to be able to connect the internet (wireless, wireline both)
because of non-existence of network-manager and network-manager-gnome

so, I downloaded both packages by using another PC, and moved to the Dell mini9.

I double-clicked network-manager~~.deb file to install it: however, I couldn't do that and it said that "Broken dependecies. Your system has broken dependecies. This application can not continue until this is fixed...."

Then, I opened Synaptic Package Manager, and found that ubuntu-minimal (1.102belmont3) was broken.

I tried to do "Fix Broken Packages" from Edit in the menu bar, then it required me to install "libpcsclite1" and "wpasupplicant".
However, as I wrote above, I cannot connect to the internet, so I cannot.

I downloaded both libpcsclite1 and wpasupplicant by using another computer and moved it to the Dell mini9, trying to install,
but again, because of broken ubuntu-minimal, I couldn't install them.

Does anyone know how I should deal with this problem?

Thank you so much.

---

### Post by coffeeaddict22 on 2009-06-28
Hi Murap,
Welcome to Ubuntu!
In summary,
  1) you've got no network access
  2) You've entered one of the forms of "dependency hell"
  3) You can't install packages.
It might be possible to fix this; however, your best bet would be to get a Live CD- or better given your machine, a boot USB- and reinstall from scratch.
The concern is why did it happen in the first place.  If you're like the rest of us, you've been playing :-)  however, it's possible it's a drive failure/ something along those lines.  Make sure you're backed up.

---

### Post by murap on 2009-06-30
Thank you so much for your reply.

I actually tried to create recovery USB by using another computer (Win XP) and the DVD, Ubuntu 8.04+ LTS Recovery Media sent by dell with the computer, in order to re-install Ubuntu.
I have to create USB's because my PC, Dell mini9(broken one), does not have DVD (CD) drive.

However, the software, liveusb-creator-ubuntu didn't work, so I couldn't create the recoery USB.

Could you tell me whether or not there are some other ways to re-install?

---

### Post by coffeeaddict22 on 2009-07-01
The USB creator software does work. I put it on a key of mine and then it kept wanting to install on everything I plugged it into for the next while...
Where did you access it?  Through System/Admin/USB Startup Disc Creator?

Essentially, you need to get about 700MB of data onto the PC.  USB is easiest; an external drive is an option.  If your network is down, that's not.  I'm not aware of a simple way of using the existing HDD to install; however, I think it is possible.  In short, the USB key is far and away the simplest, and it's known to work.  What happened when you tried?

---

### Post by murap on 2009-07-01
Thank you for your reply soon.

Sorry, I meant that the software, liveusb-creator-ubuntu, didn't work on "another PC".
In other words, I couldn't create the USB re-install key.

Firstly, I started the software, libeusb-creator-ubuntu, and it told me "there is no disc" (like the attached image 1).
But actually the disc which is provided by dell in in the PC.


After that, I just ignored the notice by clicking "continue"(right button of the image1) twice,
then, the interface (image2) appeared.

I inserted USB to the PC, and clicked "Start".
After that, the result (image2) was shown.
It seems it is successful, but it took only a few seconds to show that result, and
when I clicked the USB icon from My computer, it said that "This USB is not formatted".

Also, I inserted this USB to the Dell mini9 and tried to find "USB Setup disc creator" from System>Admin>, but I couldn't find it.

Is there any other software to create USB re-installer?


The final resort is sending back to Dell to recover it, but I don't want to do that because I bought it in Japan (I'm Japanese) and brought to Australia (I'm in Australia now).
It means I have to send my Dell mini9 to Japan, costing me high...

---

### Post by snowpine on 2009-07-01
If you want to restore your Dell Mini to the factory-preinstalled Ubuntu 8.04, detailed instructions are in this thread: [http://www.mydellmini.com/forum/ubuntu-netbook-remix/271-dell-mini-9-ubuntu-restore-iso-image.html](http://www.mydellmini.com/forum/ubuntu-netbook-remix/271-dell-mini-9-ubuntu-restore-iso-image.html)

If you want to install the latest Ubuntu Netbook Remix 9.04 (less hassle): [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by murap on 2009-07-05
Thank you snowpine,

but I don't have the account of demonoid.com, so I cannot.


Anyway, I finally could create USB re-installer by using another PC (not dell mini9) and originally attached recovery disc by Dell.

However, nothing happened when I insert the USB key to the dell mini9.

followings are the file in the USB key

A1341_UP.img
boot.msg
bootfs.img
initrd0.img
install.cfg
install.sh
ldlinux.sys
rootfs.img
syslinux.cfg
vmlinuz

could anyone give me advice to re-install?

---

### Post by ugm6hr on 2009-07-05
> **murap said:**
> could anyone give me advice to re-install?

Without an external DVD drive, I would recommend just installing 9.04 NBR.

This has all the necessary links: [http://www.ubuntumini.com/2009/04/user-guides-for-ubuntu-904-juanty.html](http://www.ubuntumini.com/2009/04/user-guides-for-ubuntu-904-juanty.html)

---

