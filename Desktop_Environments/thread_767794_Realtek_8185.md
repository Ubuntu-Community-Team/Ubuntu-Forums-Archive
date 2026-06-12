---
title: "Realtek 8185"
date: 2008-04-25
forum: Desktop Environments
---

### Post by zib_redlektab on 2008-04-25
I just installed 8.04 on my Desktop machine, which has a PCI wifi card with the Realtek 8185 on it. As far as I can tell, Ubuntu thinks it's an ethernet controller. I have no other way to get internet on that computer...All the pages I've found talking about the 8185 recommend using ndiswrapper, but since I don't have internet I can't install that :(

Does anyone have any suggestions? :confused: Last time I really used Ubuntu was Hoary, so I've lost most of what I used to know, unfortunately...

---

### Post by Claan22 on 2008-04-26
I also have a Realtek 8185, and can't get it to work properly with Ubuntu.  

Forgive my lack of terminology, but when I go into network settings, it only shows options for an ethernet port and something else that isn't useful to me, but not for my wireless card.

According to Device Manager in Vista, it's a Realtek 8185 Extensible 802.11b/g wireless device.

Strange that somebody else would have the same problem at the same time as me...

---

### Post by jimv on 2008-04-26
Hey, I had the same issue with the RTL 8185 Extensible card...is this a Gateway laptop?

Anyway, here's a blog post that I wrote up about how I got the card to work using NdisWrapper:

[http://jimvernon.com/archives/53](http://jimvernon.com/archives/53)

Also, if you cannot get onto the internet via wifi, you can try temporarily plugging your computer straight into your router/modem via an ethernet cable.  Then you can get NdisWrapper.  OR you can download the files manually here and copy them to your computer with a thumbdrive (get them both):

[http://packages.ubuntu.com/hardy/ndiswrapper-common](http://packages.ubuntu.com/hardy/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9)

---

### Post by zib_redlektab on 2008-04-26
Ok yeah, I did that, and it still says I only have a wired connection. :confused:

running ifconfig gives me eth0, eth0:avahi, and lo...

---

### Post by Claan22 on 2008-04-26
> **jimv said:**
> Hey, I had the same issue with the RTL 8185 Extensible card...is this a Gateway laptop?

Anyway, here's a blog post that I wrote up about how I got the card to work using NdisWrapper:

[http://jimvernon.com/archives/53](http://jimvernon.com/archives/53)

Also, if you cannot get onto the internet via wifi, you can try temporarily plugging your computer straight into your router/modem via an ethernet cable.  Then you can get NdisWrapper.  OR you can download the files manually here and copy them to your computer with a thumbdrive (get them both):

[http://packages.ubuntu.com/hardy/ndiswrapper-common](http://packages.ubuntu.com/hardy/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9)
It didn't work for me.

And when I type 'ipconfig' it says 'bash: no such command'.

---

### Post by zib_redlektab on 2008-04-26
make that ifconfig, not ip ;)

---

### Post by Claan22 on 2008-04-26
> **zib_redlektab said:**
> make that ifconfig, not ip ;)

Ah, sorry, been usin Windows too long I guess.

When I do 'ifconfig', I get eth0 and lo.

---

### Post by hansjuuh on 2008-05-06
(I have this problem too.)

So by installing the files from ndiswrapper, the wifi card will work?

---

### Post by Claan22 on 2008-05-06
> **hansjuuh said:**
> (I have this problem too.)

So by installing the files from ndiswrapper, the wifi card will work?

It doesn't for me.  It says that the hardware and the driver are present, but I still can't use it to connect in Ubuntu.

I'd really like to be able to use Ubuntu more, but without a wifi card it's easier to just use Vista.

---

### Post by nxain on 2008-05-06
I haven't figure this out either.  Installation went fine and the ndiswrapper says the hardware is there.  But, I can't seem to figure out how to get ubuntu to turn on the card.

---

### Post by jimv on 2008-05-07
You tried

sudo modprobe ndiswrapper?

---

### Post by yfronto on 2008-05-07
> **nxain said:**
> I haven't figure this out either.  Installation went fine and the ndiswrapper says the hardware is there.  But, I can't seem to figure out how to get ubuntu to turn on the card.

So when you run ifconfig, you're seeing the wlan interface? Perhaps you just need a frontend package like 'wlassistant' to help you out.

---

### Post by issih on 2008-09-23
Edit - wrong thread sorry

---

