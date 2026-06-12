---
title: "Converting my Laptops Connectivity into an Outbound Wireless Signal"
date: 2008-06-22
forum: Gaming &amp; Leisure
---

### Post by FinalFightFanatic on 2008-06-22
Hey everyone,

I posted this under gaming, because although not limited to my new Wii, that would be the bulk of usage for this question/answer.

I have a laptop with a very high powered Wireless Antenna I purchased from Radio Labs called the Wave-2 Ultimate with a mile range - I can pull up almost countless internew connection sources on my laptop (legally, living behind a McDonald's and a Starbucks) but I can't harness that strong connection in my Wii or any other wireless device, because my laptop is only receiving incoming signals, and I can't make it a hotspot, or wireless access point so my other devices can receive that internet service from my laptop's signal.

**[CENTER]Is there anyway, to convert my laptop into a hot-spot that actually takes those incoming signals and transmits them throughout my home somehow for my Nintendo Wii and other devices (printer, cell phone) to recognize and pick up for online connectivity?[/CENTER]**

Thank you so much for you help, I searched around the forum first and saw the admin made a couple posts, but they all concerned direct LAN input.

-Aaron :)

---

### Post by FinalFightFanatic on 2008-06-22
PS: My laptop is a new HP with an internal Wireless Card, but the Radio Labs Wave-2 USB Wireless Antenna I have is extremely high wattage and I have very strong connections from non-secured business next door...

*****I read about the WiFi MAX created for Playstation and Wii... is this something that would work or I'd need, or are there better options (free) or equipment to buy in order to achieve this goal?***

---

### Post by diablo75 on 2008-06-22
Doing this wirelessly can be done, but it is NOT easy.  I took one look at the HOWTO, and said, "No thanks."  It would be worth my time to spend the 20 or 30 bucks it takes to get the USB>Ethernet adapter available from Nintendo, and do internet sharing from the laptop via Ethernet.

If you know a fellow hacker, they might be able to help you with doing it wirelessly:

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

---

### Post by FinalFightFanatic on 2008-06-23
Thanks Diablo...
 
So you're saying there is an easier way to do this? I am not against spending the money to do it right, that's for sure - I'm just frustrated because I got the last Wii they had at WalMart, and now I have no way of getting online. 
 
**Could you, or anyone, help me out with the equipment I need to buy and set up to be able to use the strong incomming wireless signal to my laptop, and have that as an 'outbound' signal that my Wii can pick up on** (*or if I have to hard wire it to my wii, I can just take my laptop into my living room as well*)
 
Please let me know both ways... totally wireless, and maybe 'tethering' from Wii to laptop with a hardwire somehow?
 
Thanks!! :)

---

### Post by diablo75 on 2008-06-23
Internet connection sharing is supposedly easy to do via Firestarter (use Add/Remove to install it).  But I've not done this, nor do I know if it supports doing that with a wireless device (my bet is that it doesn't, nor will it ever).

You can also investigate using Backtrack 3 Beta Live CD, since it uses MadWifi drivers by default and will enable your wireless device to "Master Mode".

These are two things worth looking into if you want to solve this problem wirelessly.  But it will take a lot of time and research and I don't know exactly where to direct you.  I've tried to get someone to guide me on how to do this via the Backtrack forums, but they accused me of attempting to set up a malicious, unsecured AP that anybody could connect to, and from which I could invade their privacy by sniffing all the traffic.  They don't provide help if there is even a shred of suspicion you're going to use that information in a bad way.

The easier option, as mentioned before, is to buy Nintendo's USB > Ethernet dongle adapter:

[http://www.google.com/products?q=nintendo+wii+usb+ethernet+adapter&ie=UTF-8&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&sa=X&oi=product_result_group&resnum=1&ct=title](http://www.google.com/products?q=nintendo+wii+usb+ethernet+adapter&ie=UTF-8&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&sa=X&oi=product_result_group&resnum=1&ct=title)

It's cheap, and sure fire.  And configuring your ethernet port on your computer/laptop to share a connection across to the Wii wouldn't be hard to do.  I should add, though, that you will need to use a cross-over ethernet cable, and not a strait-through cable (they're different).

---

### Post by FinalFightFanatic on 2008-06-23
Well since my laptop gets such a strong incoming wireless signal from the hot-spots around my home, I can take it into the living room and hook up to my Wii with the crossover and the USB dongle adapter. 
 
Thanks for your help, I'm going to have to research everything... but this is an awesome starting point! :) If I have any other questions, please don't hurt me, haha...
 
-A

---

### Post by FinalFightFanatic on 2008-06-23
So once I buy the dongle for the Wii, and the crossover ethernet cable to plug into the Wii and connect to my Laptop... how do I connect the *other end of the crossover to my laptop?*
 
**...Does my laptop need any special adapters or software in order to make the *input-hole* for internet and *out-bound signal* back to the Wii?**
 
 
*Because*... I have no actual hard-wired LAN or cable coming into my home/laptop... I have all my signal derived from surrouding wireless networks. *Can I still use this method without actual hardline ethernet hookup into my latop? (**Is this compatible with Wii? I use it on my laptop, it's amazing [http://radiolabs.com/products/wireless/wave-magnum.php](http://radiolabs.com/products/wireless/wave-magnum.php))*

---

### Post by diablo75 on 2008-06-24
You should have no problem using Firestarter to share the wireless Internet you receive with your giant antenna out to your eth0 port, which is where you'll plug one end of your crossover.  The other end goes to the Wii dongle.

*Wireless Signal*>Laptop (with Internet sharing configured)> Ethernet port on laptop>cross over cable>Wii.

Piece of cake  :)

---

### Post by FinalFightFanatic on 2008-06-24
> **diablo75 said:**
> You should have no problem using Firestarter to share the wireless Internet you receive with your giant antenna out to your eth0 port, which is where you'll plug one end of your crossover. The other end goes to the Wii dongle.
 
*Wireless Signal*>Laptop (with Internet sharing configured)> Ethernet port on laptop>cross over cable>Wii.
 
Piece of cake :)
 
Awesome, I'll just google Firestarter and get that software and download it. Thanks for all your help, I'm going to try this out today maybe, I woke up with the flu and had to call off work.
 
Any suggestions on good crossover wires or software by a specific company or website? Have a great day.

---

### Post by LeoSolaris on 2008-06-24
The software is in the repo (use Add/Remove on your menu) It's primarily a front end for the firewall built into Ubuntu. (meaning it is just a pretty graphic to point and click at to control the already configured firewall that comes standard) I didn't know it made 'Net sharing easier, thats a good piece of info.

Most likely Radio Shack would have the cord.

Leo

---

### Post by LeoSolaris on 2008-06-26
[quote=FinalFightFanatic]Hey again, I just wanted to know what a 'repo' was, for the add/remove command for getting firestarter on my computer? How do I get there...
 
Would I have to mess with Window's firewall or anything with my Avast anti-virus protection, or would all of that not matter?
 
Thanks!
 
-Aaron[/quote]

Sorry it took a little while to get back to you, I am in the process of moving South, and the big day is this weekend!

Anyways to answer your question (by the way, ask it in the forum so others can benefit, too) a repo is a slang word for repository. It is the server that Ubuntu can access for new software, updates, and some piece of mind. (It's secure, and all of the software in it is screened by the Ubuntu staff to keep mal-ware out.)

Almost all of the software you will need is in the Ubuntu repo, and you can access it anytime you're online. Just open the menu where all of you're programs are (it's the first on in the upper right hand corner) and at the bottom, by default, is a program called Add/Remove. There is a seach bar in it so you can do a search for firestarter. (Be aware that I have no idea how to do what was mentioned in the thread)

If you're Ubuntu is installed on Windows with Wubi, I do not think so, but try it once to see, I could be wrong.

Leo

(It was a PM, no biggie)

---

