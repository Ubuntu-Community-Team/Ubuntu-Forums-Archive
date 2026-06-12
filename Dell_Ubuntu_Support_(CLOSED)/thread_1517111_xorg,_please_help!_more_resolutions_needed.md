---
title: "xorg, please help! more resolutions needed"
date: 2010-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jasoncowen2k on 2010-06-24
Hello Ubuntu Gods,
I've been having wicked troubles. First, I went to upgrade from 9.10 - 10.04... that messed me up big time. I scrubbed the drive, reinstalled 9.04 and could get up to 1400x1330 resolution. I upgraded to 9.10 and now can only get up to 800x600. I remembered long ago that I found a fix to this problem, but have been scouring the net to get it fixed but unsuccessful. I have a dell b120 from 2006, with a 300gb sata drive, dell monitor, 580ram. I remembered long ago that i found a great generic xorg.conf file and saved it to disk and it worked great. To tell u the truth I'm sick of 800x600! Can anyone help?

thanks for the time and consideration,
jason

---

### Post by VH-BIL on 2010-06-24
have installed a graphics driver for it? A search on the dell model shows that it has an intergrated Intel graphics card. If you have not put another graphics card in the machine (you can test this by using "lspci | grep VGA")  edit your xorg.conf file and change the driver to "intel".

---

### Post by mooreted on 2010-06-24
First of all, I don't think upgrading is a good idea, it tends to cause issues. Just my opinion, but I always do a clean install when moving to a new OS.

Sounds like you might be using the standard VESA driver. Open a terminal and try:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo dpkg-reconfigure xserver-xorg

---

### Post by VH-BIL on 2010-06-24
> **mooreted said:**
> First of all, I don't think upgrading is a good idea, it tends to cause issues. Just my opinion, but I always do a clean install when moving to a new OS.

I have always upgraded and never done a fresh install in many years. My computer boots and runs as fast as it did when I first installed it. Why fresh install and loose all your settings, applications, themes etc... when you can upgrade.

---

### Post by mooreted on 2010-06-25
Well, I do a lot of customisation and sometimes the upgrade doesn't translate well. I have had several times where an upgrade broke my system. It took me longer to fix it than a clean install. Now I backup the scripts I've modified and do a clean install. I've found it to be faster and more reliable than an OS upgrade.

---

