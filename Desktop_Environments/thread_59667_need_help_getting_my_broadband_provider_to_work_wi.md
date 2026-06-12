---
title: "need help getting my broadband provider to work with ubuntu"
date: 2005-08-24
forum: Desktop Environments
---

### Post by blacklantern on 2005-08-24
Has anyone ever heard of insight broadband internet? If not their website is [here.](http://www.insight-com.com)  They've given me an installation disc that I need to use to activate the service, but I'm trying to move entirely to ubuntu. I'm not sure how to get my internet working of I have ubuntu. 

I guess a good followup question would be this: If I have a roommate that uses a windows machine, and I'll be using a linux machine, will it matter if we're on the same router? Finally, id there a way to make sure that my internet works whether I'm on windows or linux?

---

### Post by 5-HT on 2005-08-25
Hi, never heard of insight before but may be able to help out a bit.

First off, the installation disc may have a few functions such as:
1. Activating the service and registering your MAC address (if insight binds MAC's to accounts..some ISP's do, some don't) 
2. Installing any insight related software
3. Installing drivers for usb modems (if you're running a USB connection)

About registration, the software may only run on a windows machine. However, you mentioned that you're running a few pc's off of a router, so your best be would be to run it off the windows box to get the account set up (which hopefully should work fine).
Most likely if insight needs to register a MAC, it'll use the one from the router (depending on whether or not they allow routers. I think most ISP's don't mind, but if they do then the software may try to grab the MAC of the NIC in the computer thats running the software and then wouldn't complete successfully if you're running through the router).

If that still doesn't work, I'd suggest just giving them a call to manually activate the service and give them the MAC.

In terms of installing software, that should be no prob as you can use Firefox (or whichever browser) and whatever email client you'd like.

In terms of drivers, if you're running of a router most likely you're using an ethernet connection? 
If that's the case there's no need to install any as the only one you'd need would be for your NIC, but hopefully that'll already be automatically detected and configured by unbuntu.



Hope you get it working.

---

### Post by blacklantern on 2005-08-25
Insight does in fact bind mac addresses to accounts. I found this out when I switched apartments. My first account was disabled and a new one was created for my new apartment. When I tried to use the same cable modem, the registration software wouldn't let me go through at first because the modem's MAC address was bound to my old account. I called and got that fixed.

The modem can be connected using USB, but I'm just using cat-5 ethernet cables, as you guessed. I guess I'll try again using the ubuntu live CD and seeing what happens. If anyone else can give advice on this issue, please feel free to do so.

---

### Post by Galoot on 2005-08-25
I can't answer the software questions, but I've never heard of several PCs running different operating systems accessing the net through a single router giving anyone any problems.

---

### Post by blacklantern on 2005-08-25
Thanx for all your help--I'd figured that the internet wouldn't work right away with the liveCD, which I'm running now. Looks like I'm all set.

---

