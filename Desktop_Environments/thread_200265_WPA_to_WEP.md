---
title: "WPA to WEP"
date: 2006-06-20
forum: Desktop Environments
---

### Post by analogdevices on 2006-06-20
I have a netgear wireless router (don't know the model, but it's white with one antenna and does _not_ have a blue light on top) secured with a WPA password. since ubuntu can't handle WPAs, I've been trying to change it to WEP. has anyone else gone through the same process with their Netgear router? if so, please help me out.

---

### Post by icheyne on 2006-06-20
Ubuntu does handle WPA. It's quite easy with my RT2500 wireless card, but I had to alter a config file.

You reset a router's password, you generally have to press its reset button and start from scratch.

---

### Post by shof2k on 2006-06-20
You should find the routers model number on a silver grey sticker on the bottom or back of it.  If it's fairly recent (<2 years), you should be able to choose encryption on the web set up page.

Ubuntu does support WPA although with some tweeking in my case. I'm running a netgear dg384v2 with a safecome dongle with automatic wpa. 

I would seriously discourage you from using WEP, there are programs than can break WEP in mins.  WPA is a much better alternative for now, unless you don't mind the world and thier dog sharing your network :)

---

### Post by compmodder26 on 2006-06-20
Give network-manager a try.  It's in the repos.  Very simple to set up a wireless connection with wpa through it.

---

### Post by DeeZiD on 2006-06-20
I did this on a toshiba notebook with intel ipw3945 wireless:

Installed network-manager-gnome through synaptic.
Then started nm-applet and did select my wpa-encrypted wlan and entered the password. :o 


regards Dennis

---

