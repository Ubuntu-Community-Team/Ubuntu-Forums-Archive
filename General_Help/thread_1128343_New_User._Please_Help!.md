---
title: "New User. Please Help!"
date: 2009-04-17
forum: General Help
---

### Post by darklotus8586 on 2009-04-17
I installed Ubuntu on my desktop at home last night, but I encountered a few problems. :(

First, I could not access my external hard drive. It kept saying "failed to mount drive". Nothing I tried would work. 

Second, I could not connect to the internet. I went to Applications>Network Tools, but found nothing useful. I don't know my SSID or anything like that. I have cable internet and use a Linksys router. I'm just wondering how I can pull up the list of available networks. 

Thanks in advance for any help!

---

### Post by cariboo on 2009-04-17
A little more info would be helpful. How are you trying to connect? Wired or wireless?

Jim

---

### Post by darklotus8586 on 2009-04-17
It's wireless using a linksys router. 

I think this is the wireless card I have installed on my desktop: Linksys Wireless-G PCI Card WMP54GS with SpeedBooster. I'm on the computer on campus right now so I can't check.

And I think I may have found a solution for the mounting problem, but I can't try it until I get home from work tonight.

Do I need to install the wireless card on Ubuntu or should it already be set up? The problem with that is I don't have the installation CD. However, I do have the installation files saved on my external hard drive. The same external hard drive that I'm having trouble mounting. 

Thanks.

---

### Post by DenysT on 2009-04-17
First try connecting to the router with an ethernet cable. Then in the address bar of Firefox type in 198.162.1.1 (Linksys standard home page) and you will then be able to access all the info about your router. Get the SSID and any security settings you will need to connect to wireless side. I recommend changing default SSID, usually just Linksys, to something else and setting up WPA security to keep others from accessing your network.

NOTE: *The router will ask you to login and if you have not set any passwords or names (i.e. you are using it straight out of the box) leave the Username blank and the default password is "admin" without the quotes.*

Once you have all the info see if you can connect to any URL in Firefox, if not you need to set your router up to access the cable modem, this is easy to do especially with cable as most use dynamic addressing. Not knowing which Linksys router you have I cannot exactly tell you where to find all this as all the router companies seem to modify their pages with each new router.

You should also check to see if the SSID is broadcast or not. If the SSID is not broadcast you will have to enter it in the connection (this is really more secure), if it is being broadcast and it is not coming up in the list of wireless networks then the problem lies with card being configured properly in Ubuntu. The installation files on your external drive will do you no good as they are probably Windows and MAC only more than likely.

---

