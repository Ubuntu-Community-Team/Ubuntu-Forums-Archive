---
title: "Beryl and 3D Installation help?"
date: 2007-10-11
forum: Desktop Effects &amp; Customization
---

### Post by rialto on 2007-10-11
I am brand new to Linux and Ubuntu.  Please help me =)

I am currently using a dual boot system with Windows XP and Ubuntu 7.04.

My system is a Dell Inspiron 8200 with these stats:
2.0Ghz Intel CPU
1 GB RAM
64MB Nividia Go Geforce Video Card
120 GB Hard Drive space

The installation of Ubuntu 7.04 was successful and all hardware works.  I have tried to enable 3D acceleration but as soon as i reboot, the computer gets into the ubuntu operating system and is completely black.  I know that the computer has great 3D capabilities because I've played games such as Final Fantasy XI online with this system without any problems.

My question is how do i get 3D working on Ubuntu with my system?
Where do I get the latest Beryl? 
Which Beryl is best suited for my system?
Is there an easy tutorial for ubuntu noobs like me to install beryl?

Thank you for reading this post. =)

---

### Post by overdrank on 2007-10-11
> **rialto said:**
> I am brand new to Linux and Ubuntu.  Please help me =)

I am currently using a dual boot system with Windows XP and Ubuntu 7.04.

My system is a Dell Inspiron 8200 with these stats:
2.0Ghz Intel CPU
1 GB RAM
64MB Nividia Go Geforce Video Card
120 GB Hard Drive space

The installation of Ubuntu 7.04 was successful and all hardware works.  I have tried to enable 3D acceleration but as soon as i reboot, the computer gets into the ubuntu operating system and is completely black.  I know that the computer has great 3D capabilities because I've played games such as Final Fantasy XI online with this system without any problems.

My question is how do i get 3D working on Ubuntu with my system?
Where do I get the latest Beryl? 
Which Beryl is best suited for my system?
Is there an easy tutorial for ubuntu noobs like me to install beryl?

Thank you for reading this post. =)

Hi and welcome, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by cacharreo on 2007-10-11
Try this:
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by rialto on 2007-10-12
thanks overdrank! i'm finally back into ubuntu after a few tries, but 3D still doesn't work.  I'm wondering if I should install new nvidia drivers.  If I should, how do i do it?

according to all the posts i've read up till now, it also sounds like i have to get my 3D working before installing beryl also.  So i think i'll get my 3D working before I start on Beryl Installation.  Thanks for the replies and help! You've helped so much!

rialto

---

### Post by overdrank on 2007-10-12
> **rialto said:**
> thanks overdrank! i'm finally back into ubuntu after a few tries, but 3D still doesn't work.  I'm wondering if I should install new nvidia drivers.  If I should, how do i do it?

according to all the posts i've read up till now, it also sounds like i have to get my 3D working before installing beryl also.  So i think i'll get my 3D working before I start on Beryl Installation.  Thanks for the replies and help! You've helped so much!

rialto

Hi and yes you need to install the drivers for your card. What is the model of your card?
lspci in the terminal will give you the information. terminal is located under applications, accessories.

---

### Post by Pumalite on 2007-10-12
How about System>Administration>Restricted Drivers Manager>Enable

---

### Post by madmatrixz3000 on 2007-10-12
Personally, I would say that you should not worry about 3D if you can last a week without it.  If it is vital, then I suggest upgrading to Gusty Beta and then Gusty full next thursday.  Gusty solved amost all the 3D problems and give noobs like us an easy GUI interface to change the xorg settings without crashing.

---

### Post by rialto on 2007-10-13
my video card is the nVidia Geforce4 440 Go card and I've read on another post that updates on this card is tricky and drivers from the nvidia website will not help.  I'm starting to wonder if I should just wait for a week and then install the full version of the new Ubuntu.  =)

Each time I enable the 3D accelerated graphics drivers through System>Administration>Restricted Drivers Manager, I get the same black screen after I reboot.  It's the same problem I've been having before, so I believe that the drivers on this computer isn't working for the 3D.  I've done a few google searches for the drivers for this video card for Linux but have been unsuccessful.

Thanks for helping me through this.  I'm learning tons more about linux by just reading through other people's experiences with video and beryl issues.

---

