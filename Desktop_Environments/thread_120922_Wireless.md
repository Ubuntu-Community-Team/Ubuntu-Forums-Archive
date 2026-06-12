---
title: "Wireless"
date: 2006-01-23
forum: Desktop Environments
---

### Post by Monkey12 on 2006-01-23
I know this is probably a repost but I couldn't find any forums that really told me what I needed to do. Also, i'd like to say that i'm a total linux newb. I've only been using ubuntu for about two hours, and previously i've briefly used mandrake and gentoo but not very extensively. So please be patient with me.

I just installed Ubuntu 5.1 on my Compaq presario m2105us notebook. Everything seems to be working fine except for my wireless adapter (broadcom BCM8406). I know that i'm probably going to need to use ndiswrapper, but I have no idea how to install it, and after that I may need help installing the driver. But i'll start with just getting ndiswrapper installed.

Any help would be greatly appreciated.

---

### Post by dodgeman79 on 2006-01-24
I'm a newb too, been using for Ubuntu 5.10 for about 4 days.  my card (d-link dwl-g650) was recognized.  System -> Administration -> Networking.  check there and see if your card is there.  If it is then use the properties and activate buttons to configure and start up your card.

p.s. if you've already done this great.  I don't even know what ndiswrapper is and how it works.  but I've see it around.  good luck

---

### Post by Tiede on 2006-01-24
I too have a broadcom driver... My guess is your *will* have to use ndiswrapper to configure your card. No worries, it takes less than 5 minutes. if you are like me, I'd suggest installing the ndisgtk package instead of teh actual ndiswrapper (ndisgtk is graphical and it will automagically install ndiswrapper). 
Also, check out this link. IT worked for me: [http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wireless+modem](http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wireless+modem)

---

### Post by manicka on 2006-01-24
There may be some helpful information here

[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

---

### Post by Monkey12 on 2006-01-24
Thank you all for your help. Everything you've shown me will be very helpful in installing the driver itself, but at this point i'm not even sure how to install ndiswrapper. The instructions that come with it aren't very good for a new user.

---

### Post by gosh on 2006-01-24
You will find ndiswrapper in System->Administration->Synaptic Package Manager.
Click ndiswrapper to install and it will be done automatically for you.

To set up ndiswrapper to work with you network card read this wiki:
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

---

### Post by Monkey12 on 2006-02-12
Alright, i've got it working now. I think it was just a matter of finding the right driver. I have only one more problem. I have to modprobe ndiswrapper every time I start my computer to get the wireless working. What do I need to do for my wireless to load during startup.

---

### Post by gosh on 2006-02-12
to do that:

$sudo ndiswrapper -m

and do

$sudo gedit /etc/modules

and add

ndiswrapper

to the end of the file.

---

