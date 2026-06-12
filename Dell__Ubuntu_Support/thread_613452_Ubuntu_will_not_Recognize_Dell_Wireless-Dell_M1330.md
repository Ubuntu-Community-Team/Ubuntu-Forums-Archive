---
title: "Ubuntu will not Recognize Dell Wireless-Dell M1330"
date: 2007-11-14
forum: Dell  Ubuntu Support
---

### Post by flamenko on 2007-11-14
I have installed Ubuntu on my M1330 and it does not recognize my wireless card, the Dell 1505N card.

Can anyone assist here or relate if they have had any success with this card?

---

### Post by maldojr88 on 2007-11-15
well son....let me tell you this 
probly one of the most tedious things in linux(any distro)
is to make the kernel recognize your wireless card...
after you complete this..however ...i can promise you you 
will learn alot about your computer and about linux...so hang in there 
and dont give up...also dont get discouraged...not every one struggles..


ok so here is a simple overview of what you need to do...

basically the problem is that the kernel doesnt have the drivers for 
your wireless card so that means it cant communicate with it..
the kernel just knows its there...but it can talk to a metal object without
knowing how it works. Usually all these wireless cards pc's have come with drivers for windows operating system only...
meaning that only windows knows how to communicate with that device. 


So there is a linux program called 
ndiswrapper

the name is kind of crazy but its basically simple wat it does...
it just takes the windows drivers and converts them to linux drivers
that the kernel can use. 
So you will need to get this program....( you will have to google it and compile it, ask if you dont know how to do this) and get the drivers for you wireless card...

but basically just google ndiswrapper and start from there...
its the program that will get the thing working...ndiswrapper actually has a forum just for wireless cards...so just google it and it will be clear wats the main page....
good look and ask questions...even the simplest ones
were all here to learn and to help each other

---

### Post by fisting_mayfield on 2007-11-15
Mine worked out of the box.  I'm using it right now actually.  Can't see why you'd need to battle with ndiswrapper.  Have you selected 'wireless' by clicking on the icon near the clock?

---

### Post by flamenko on 2007-11-15
I have installed NDIS and then downloaded the executable and extracted it within Ubuntu.  I went to system/admin/wireless drivers and then installed bcmwl6. It tells me it cannot see if hardware is present yet says 'hardware present: yes (confused)

How the heck you got it to work out of the box with the 1505n is beyond me.

So anyway....when I check to see if the driver is installed, it apparently is but not turned on. Thoughts??

Oh and further...I havent got the wireless option in the network connection icon by the clock.

---

### Post by Skuzniak on 2007-11-15
Seems like a rather silly question, but is your wireless switch turned on? My Vostro 1400 shows a wireless card installed with the switch turned off, but it is unusable until I move the switch to the on position.

---

### Post by flamenko on 2007-11-15
Yup turned on.... I just confirmed through bios as well.

---

### Post by xxsaskexx on 2007-11-23
I'm in the exact same boat.  Tried everything and Gutsy still does not want to recognize the card at all.  Network manager doesn't show any wireless option.

---

### Post by jdelaros1 on 2007-11-24
The Dell 1505 wireless card is a Broadcom card, which will not be recognized by Gutsy since it requires a proprietary driver. Some 1330 configs have an Intel wireless card, those will work out of the box.

---

### Post by xxsaskexx on 2007-11-24
I see.  I was reading somewhere that the 1505-n worked out of the box.  I guess ndiswrapper is the way to go, but I've used the GUI with the drivers provided by Dell and no dice.  Tried various methods and scripts provided by the forums and still nothing.  Anyone get their 1505-n working?

---

### Post by beamur on 2007-12-02
I have Vista and Ubuntu dual-booting.  I am having an issue with Ubuntu not recognizing my wireless card.  I am also not able to get the WLAN (Sprint) card working either.   Any suggestions?

---

### Post by madamore on 2007-12-02
visit this web...
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I think this might help you.

I have a compaq notebook with broadcom wireless mini pci card and work perfect adding these drivers.

No need of ndiswrapper!

---

### Post by mcdonji on 2008-02-15
I have the same trouble. Dell m1330. Dell Wireless 1505 Wireless-N Mini-card did not work out of the box. I guess I'll start digging.

---

