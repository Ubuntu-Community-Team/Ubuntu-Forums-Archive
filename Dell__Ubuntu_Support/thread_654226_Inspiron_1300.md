---
title: "Inspiron 1300"
date: 2007-12-30
forum: Dell  Ubuntu Support
---

### Post by the_sorrow on 2007-12-30
I have problems on Gutsy with my wireless card on an inspiron 1300, it tells me that the driver is not avaible because microsoft wants to rule the world or something like that, can anyone help please?? it is the only thing  stopping me from changing comppletly to linux.

---

### Post by VorDesigns on 2007-12-31
What is the wireless card manufacturer and model?
Do you get any messages when you insert the card?  If so, what are those messages.
what version of Ubuntu are you running?

---

### Post by the_sorrow on 2007-12-31
It is a broadcom 43xx chipset family 
I get this message:
Enable the Firmware?

Firmware for Broadcom 43xx chipset family

While the bcm43xx driver is free, it relies on proprietary firmware. Without that you will not be able to use your wireless card.

I am running 7.10
I have problems to with the codecs for mp3, mp4 and so on I need help urgently!!

---

### Post by VorDesigns on 2008-01-04
Take a look here, [http://www.linuxquestions.org/questions/linux-networking-3/howto-broadcom-bcm43xx-driver-463002/]("http://www.linuxquestions.org/questions/linux-networking-3/howto-broadcom-bcm43xx-driver-463002/").
This is a Dapper document but it might help; [WifiDocs/Driver/bcm43xx/Dapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper").
Then again, the Feisty doc might be closer to what you need; [WifiDocs/Driver/bcm43xx/Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty").
You mentioned your driver problem; [Debian forum's HowTo: Broadcom BCM43xx Wireless Card]("http://forums.debian.net/viewtopic.php?t=7949&sid=9ce9440fbd72a1aad0432863a7337fbd").
Not sure how to help with the codecs, I was prompted by the player when I needed stuff and was able to update.  Someone else here might be able to help you better with that.
Found another one that might help; [http://ubuntuforums.org/archive/index.php/t-434946.html]("http://ubuntuforums.org/archive/index.php/t-434946.html")

---

### Post by the_sorrow on 2008-01-04
I solved the problem, using the ndiswrapper and some information from the second link you gave me, the only problem I'm having is the audio codecs

---

