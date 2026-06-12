---
title: "Hi need help configuring my wirless network ?"
date: 2006-09-18
forum: Desktop Environments
---

### Post by cobbweb on 2006-09-18
Hi, 
   I posted this question here

 [http://ubuntuforums.org/showthread.php?t=260502](http://ubuntuforums.org/showthread.php?t=260502)

 I can' seem to figure out how to configure you wireless card to pick up the internet. It's been a while sice I have configured a wireless linux machine and need some help. Any help is welcome, 

 Thanks, 

  Cobbweb

---

### Post by wieman01 on 2006-09-19
Can you please post this file:
> /etc/network/interface
That'll help. Also unhide your ESSID so that we can start with the easiest possible setup. I assume you don't use encryption, is that correct?

---

### Post by nullmind on 2006-09-19
Well, if the card works but just won't get a connection, what does this do:

```

ifconfig eth1 up
iwlist eth1 scan

```

Assuming that the device is called eth1 (it could be eth0, but usually is eth1) This should print out some information about the surrounding wireless networks available. If this prints out the network correctly, I would reccommend just trying the network-manager interface:

```

sudo -s
apt-get install network-manager network-manager-gnome

```

Press ALT+F2 afterwards and enter **nm-applet** to run the applet.

Once network-manager is wroking you can just left-click the menu applet icon and the wireless networks should be available in a list.

I'm not sure if this matter, because I have a poorly supported card (Broadcom 4318 uses the bcm43xx driver) but sometimes I do this to help "reset" the device:

```

rmmod bcm43xx
modprobe bcm43xx
ifconfig eth1 up

```

That won't do anything if you don't have a Broadcom card, so find out what driver the card is using (not sure how to do that)

Cheers,
Kristopher

---

### Post by cobbweb on 2006-09-19
Hi,  
 
 It was a brodcom card, and I was able to get it to work by using a Windows driver... he he.. anywho, thanks for the helpful starts. :)


 Cobbweb

---

