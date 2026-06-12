---
title: "Dell  Latitude E6500 - problems with hibernation, touchpad and virtual consoles"
date: 2008-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by googlorenz on 2008-12-16
Hi,

a few days ago I received my new Latitude E6500. The laptop has the following specs:
Intel P8400 Processor
250GB Sata HDD
Intel WiFi 5100
Intel 4500Express Chipset Graphics
1440x900 display
2 GB Ram
Built-In 0.3 MP Webcam

Using the alternate install cd, I installed Ubuntu 8.10 Desktop Edition on it (or rather, on an encrypted partition). Most things work perfectly fine out of the box.:smile:
However, I have a few problems ](*,) and was hoping that you guys could help me resolve them:

1.Hibernation does not work: When I start the computer again, after I told it to hibernate, it just does a normal boot.

**<solved>**
2.I cannot configure the touchpad properly. I installed gsynaptics using "sudo apt-get install gsnaptics". Whenever I try to start it, it tells me that I have to set SHMconfig to true in the xorg.conf file. However, my /etc/X11/xorg.conf is completely empty.:confused:
**</solved>**

3.Sometimes when I switch to the virtual consoles, the screen just flickers and does not show any text and remains so until I switch back to X (CTRL+ALT+F7). At other times everything works properly. I have no clue what is going on there...

4.The webcam does not work properly. When I use cheese, it only works with the resolution set 160x120. Higher resolutions don't work.

Thank you for your help!=D>

PS: I am new to linux (this is my first linux installation) and therefore may not understand some advanced linux terminology. ;)
PPS: If you require any further information, feel free to inquire!

---

### Post by falcon61102 on 2008-12-16
Welcome,

Well, I can't help you with all the questions, but with question # 2 with the touchpad I may be able to.

It seems that gsnaptics relies on SHMconfig to run properly and it must be manually configured.  If you take a look at this page:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

You'll see about half way down the steps to getting SHMconfig to work.  If you have any trouble with this step or it does not work, post back and we'll work through it.

---

### Post by googlorenz on 2008-12-17
@falcon
thank you very much, problem no. 2 is solved. :)

@all
has anybody got ideas concerning the other three problems :?::?::?:

---

### Post by googlorenz on 2008-12-21
*push* ;)

---

