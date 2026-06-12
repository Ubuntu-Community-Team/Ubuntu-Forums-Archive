---
title: "Want to &quot;Upgrade&quot; from Windows to Linux, but have a problem"
date: 2009-05-10
forum: General Help
---

### Post by imtheguido on 2009-05-10
Alright, so I really want to get rid of this PoS OS known as Windows XP, now that I'm no longer playing games that require it.

My problem is, My computer is in the basement of the house, and the only access I have to the internet is wireless. I have a WMP110 Linksys wireless card. I can't move my computer because my cousin will freak out if I try to hook directly into the router rather than use the wireless. I have an external Hard drive that I can put files onto so I can get my wireless card installed once I switch over to Ubuntu 8.10, but I am worried that the system will not have native drivers for the card as I have seen lots of issues with this particular card and it not working with 8.10 out of the box. Meaning, I wont be able to connect to the internet to get the drivers or programs I need to install through the update and through the update program within ubuntu.

Any ideas on how I should go about this, or am I screwed and stuck with this PoS OS?

---

### Post by scottuss on 2009-05-10
Download the 9.04 image, burn it to CD and try it out live first, this is the kind of thing it's meant for! :)

---

### Post by bacardiandwatermelon on 2009-05-10
What type of wireless card do you have?

---

### Post by imtheguido on 2009-05-10
Its a Linksys WMP110 Wireless Card. Thank you for the idea for trying the live version! I will give that a shot.

---

### Post by danwood76 on 2009-05-10
I think that card has an atheros chipset so should work out of the box!
Download a live CD and test it out!

---

### Post by gradysghost on 2009-05-10
Well, I see two options for you here, each of which introduces some amount of effort on your part.

The easiest of the options is probably going to involve you hauling that computer to a place where you have a network cable available, plugging it in, installing the wireless driver through the restricted hardware driver manager or whatever other means you prefer (plenty of articles here on that, but post if you need help anyway), and then hauling it back into the basement.

The other option is to follow a guide like [this one]("http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd") to make a custom LiveCD that will install the wireless drivers upon install.  I believe this method requires that you have a functional install with network access before you begin, so it may not be the one for you.  Also, this method demands a pretty high level of Linux knowledge.  I'm not sure exactly where you stand on that.

---

### Post by danwood76 on 2009-05-10
The custom live CD requires linux to build it!
So thats a lot of use.

With any luck the card will be supported by ath5k which is included by default.

---

### Post by imtheguido on 2009-05-10
Turns out, I dont have a CD available right now to burn the 9.04 install disk to run the live version.

And I cant haul my computer closer to plug in with an ethernet cord because my cousin wont let me. Its his router and for some strange reason, he refuses to let me plug directly into it. I wont event mention him monitoring my downloads, and any time he sees a high ping, he turns off my wireless because he assumes I am downloading some sort of torrent which he doesnt approve of.

Grrr... anyways. I have an older 8.10 Intrepid that I ran on my old computer, but that CPU was an Intel Pentium 4, and this one is an AMD 3000+ so Im not sure if that will work. I dont remember if that was a 32 or a 64 install. :/ Any ideas?

---

### Post by danwood76 on 2009-05-10
An intrepid CD should be fine, but the wifi drivers arent as good on there so it might not be a fair test.

Just kick your cousin, or hack into his router and turn his network ports off :P

---

### Post by imtheguido on 2009-05-10
I tried it, and it ran fine, but like you just said, the wireless was not supported. But you say that 9.04 should have the correct support for the card? I will have to wait till he wakes up to get a blank CD from him so I can try the live version of that.

---

### Post by gradysghost on 2009-05-10
> **imtheguido said:**
> I tried it, and it ran fine, but like you just said, the wireless was not supported. But you say that 9.04 should have the correct support for the card? I will have to wait till he wakes up to get a blank CD from him so I can try the live version of that.

Hopefully, Fascist Cousin will allow that to happen.

---

### Post by danwood76 on 2009-05-11
> **imtheguido said:**
> I tried it, and it ran fine, but like you just said, the wireless was not supported. But you say that 9.04 should have the correct support for the card? I will have to wait till he wakes up to get a blank CD from him so I can try the live version of that.

If you go back into the liveCD and click system -> Administration -> Hardware Drivers is anything listed in there?
I think the open source atheros driver (ath5k) is disabled from the intrepid CD and requires you to install that package manually but it is on the CD in a modules-backports package (can be installed through synaptic from the administration menu)

The alternative is that the madwifi driver is required which is like the closed source version of ath5k and I thing that requires an internet connection to get it installed.

---

