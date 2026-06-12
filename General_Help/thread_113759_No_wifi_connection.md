---
title: "No wifi connection"
date: 2006-01-07
forum: General Help
---

### Post by MikieEars on 2006-01-07
I just installed Ubunutu 5.10 and installed my card with ndiswrapper.

I can see that its showing networks in the network settings. I select my network set the wep key, and set it to hex, and also dhcp

But it will not let me on the internet.

It says that "wlan0" is active

also we see that it looks liike everything says ip6. Is there a way to change that? I know alot of things are not using ip6 so is that possibly whats wrong? 

I searched the forums and could not find a similiar problem. it seems that everyone who uses ndiswrapper after configureing it gets connected.

I have a belkin F5D7010 card. 

We are using a laptop
any help would be much appriciated.

---

### Post by HokeyFry on 2006-01-07
download wifi-radar and see if you are getting a connection from anywhere. There is a debian package for it but unless you can temporarily connect to the internet with your laptop, here is the source:

[http://www.bitbuilder.com/wifi-radar]("http://www.bitbuilder.com/wifi-radar")

The site tells you what you must have installed and has installation instructions. If you can't get that installed here is what you should try:

open a console, type "ndiswrapper -l" to see what your driver is called.
type "sudo ndiswrapper -e driver", where driver is the name of the driver. 
**NOTE** THIS DELETES YOUR DRIVER FROM NDISWRAPPER!!

Follow the directions in this thread I wrote:
[http://www.ubuntuforums.org/showthread.php?t=98709]("http://www.ubuntuforums.org/showthread.php?t=98709")

It is probably what you did to get the card to be recognized in the first place, but to be safe, follow the guide to the letter.

If it works now, enable the Ubuntu repostiories (don't forget the universe and multiverse repositories as well) and download wifi-radar.

---

### Post by MikieEars on 2006-01-07
we just tried doing what you suggested, wifi radar showed signal strength of my network. but when we clicked connect it can't get an ip address any more thoughts?

---

### Post by Jammy_Stuff on 2006-01-07
Are you sure your network is DHCP? If it is, make sure you don't have MAC filtering enabled on your router.

---

### Post by MikieEars on 2006-01-07
Ya we have checked that, router mac filtering is disabled. Still the same issue, only this time it says just working not even aquiring ip address. computer and router are defenitly configed for DHCP. We are currently trying to find out if we can add a repository on the one laptop that doesnt have ethernet connection to get wifi-radar installed there, origonal isnt working right when we use chmod +x wifi-radar on the folder or files even with sudo nothing happens, still doing what we can any suggestions?

Thnx Greg/MikieEars

---

### Post by MikieEars on 2006-01-07
wow hahahahahahaha all i had to do was restart the coputer.


thanks for all  the help guys, i believe i'm gonna write a read me file for proplr doing a step by step by step install of what we did

---

