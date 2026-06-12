---
title: "Gutsy, Broadcom, Fwcutter."
date: 2007-09-04
forum: Dell  Ubuntu Support
---

### Post by IanKoro on 2007-09-04
So I've been installing Gutsy Tribe-5 today, and it's been going pretty well, (my NIC actually works!)... however, my wireless card doesn't, and I don't entirely remember how to get it working again.

I have a Dell Inspiron 1420, which has the Dell 1390 Broadcom card. Ndiswrapper wouldn't work with it, as I only had Vista drivers for it. But I was able to get the driver working with fwcutter previously.

With Gutsy, the restricted modules manager is doing lots of things for me, which is nice, but then I got to the part where it asks for firmware (this part really needs to have an explanation with it, I can't imagine how a beginner would have any idea what this was asking for). I remember I had to obtain the firmware before, I think I may have had to somehow copy it off of the driver disk I have, only I can't find detailed instructions anywhere.

When I try to install the firmware available for download, it downloads, and then nothing happens. Still claims the module is disabled with no further info.

I'm sure this isn't that complicated, in fact, I probably did it before with feisty. But I haven't found anything with an explanation... I'll keep looking.... any ideas?

---

### Post by Jamie Jackson on 2007-09-04
I think there's a bug in the current fwcutter-43xx package. However, you CAN use ndiswrapper. Take a look at this [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). The associated forums post is [here]("http://ubuntuforums.org/showthread.php?t=475963")

---

### Post by nermalthecat on 2007-09-05
Are you sure you have a Broadcom wireless card? I'm pretty sure that the default is an Intel wireless card, in which case you don't need fwcutter, since there is a linux driver.

---

### Post by Jamie Jackson on 2007-09-05
I know that some Dell laptops come with either a Dell 1390 (Broadcom) or an Intel device. For instance the D620 (which I have) can come with one or the other.

In any case a "lshw -C network" or "lspci | grep Broadcom" will sort that matter out quickly.

---

### Post by Sand Lee on 2007-09-05
See this post from Gutsy Forums:
[http://ubuntuforums.org/showthread.php?t=540622](http://ubuntuforums.org/showthread.php?t=540622)

---

### Post by jardo on 2007-10-10
i have your same problem...my dell 1390 wireless card doesn't work on gutsy,and as u i followed instructions given by restricted driver manager. but after installing everything i can't get internet...also if my wireless card see the access point...i can't get over internet..i tried in all ways...i hope they will fix it with the stable release

---

### Post by TimTang on 2007-10-26
:-k Hi 

I installed Gutsy a few days ago and everything went well including recognition of my wireless card and installation of restricted drivers as well as fwcutter. The wireless interface is there (which I think is very slick by-the-way) and I can see all available Access Points as well as there relative strengths. All I have to do is select the one I want and off to cyberland I go... well not quite:

The problem I'm having is when I select the router I want, I'm prompted for the "Passphrase" (I've got the setting on "Rome"). I enter the "Passphrase" and the icon on the taskbar changes to a couple of whirling balls, which I presume indicates the connection is being negotiated. This goes on for a fairly long time (too long) and then I'm prompted for the "Passphrase" again. Basically I'm stuck in an infinite loop of supplying the "Passphrase" over and over and over and......

I know I'm not getting the Passphrase wrong ( I'm sure I got it right at least once in the thousand or so times I've entered it ). I've even tried it with dashes ( xxxx-xxxx-xx) and that didn't work either. I went through the entire "WifiDocs/WirelessTroubleShootingGuide" and that didn't solve the problem either, but it wasn't a waste of time because the guide was very educational and well written. I'm not receiving an IP address and I cannot ping the router, it would appear however that I CAN ping the ISP, which makes the problem even weirder.

Does anyone have any idea how to resolve the problem. Everything seems to be working OK but what makes it so frustrating is how close I am to getting on the internet but I'm not-quite-there.

Any advise would be greatly appreciated.

---

### Post by jardo on 2007-10-26
try with ndiswrapper...i solved with that :(
here i wrote the bug...

[https://bugs.launchpad.net/ubuntu/+bug/153683](https://bugs.launchpad.net/ubuntu/+bug/153683)

---

### Post by ukripper on 2007-10-26
I use wlassistant with broadcom wireless. fwcutter works fine but on edgy i used ndiswrapper.

---

