---
title: "X server killed the graphics card?"
date: 2007-03-17
forum: Desktop Environments
---

### Post by Maxsilver on 2007-03-17
I've been using Ubuntu Linux in a dual-boot setup for quite some time. Quite often, I will go through the work of setting up Compiz / XGL for the desktop effects. This works quite well, until an Ubuntu update comes through and kills X server (will show the dreaded "X server failed to startup" screen)

Normally, I just switch to Windows for a day or two while I fix the xorg.conf.

However, last time I decided to start with a clean Fawn Herd 5 install, and let the integrated "Desktop Effects" menu take care of it for me. click a button, get desktop effects. Worked great for a few weeks.

Then, last night I downloaded the latest updates, and it gave me a message saying I had the wrong graphics driver installed (the nVidia binary blob from their site). I didn't think much of it, since I had been using that driver just fine for weeks.

This morning, X server couldn't start (not unusual) but it didnt show a error message either. Nothing. 

I switched over to the onboard video, to get to a BIOS screen, and I can't get the card to display anything. The compy still boots into windows fine, and everything seems to work except the PNY graphics card.

However, the card's fan still spins up. And I find it odd that it would stop working over that (its hit that screen before no problem)

And it's not the power supply. (The box says 300w minimum, but it never gets warm, and I've tested it with all Hard Drives / CD drives disconnected and such, still the graphics card wont start)

And the card is still relativitaly new, just got it about two to three months ago

If anyone has any suggestions on how I could get this card working again, I would greatly appreciate it.



System Specs
-----------------------------------
AMD Athelon 64 3200+ (2.01ghz)
1024mb Ram
PNY nVidia 7300 GT (256mb Ram)
nVidia 6100 integrated graphics (usually disabled, until the PNY card died)
300Watt Antec Power Supply

---

### Post by hal8000 on 2007-03-17
I have known graphics cards to stop working through loose or dirty contacts on the agp or pci connectors.

What I suggest is power off the computer, unplug from the electric supply and remove your case and graphics card. Dont try cleaning the contacts, just removing and reinserting is enough to clean the contacts (make sure also that you are earthed) you dont want to zap your card with body static.

After that reconnect. If it still doesnt work is it being detected by linux?
Try 
lspci -vv

if all else fails, you are probably still under manufacturers guarantee :)

---

### Post by Maxsilver on 2007-03-17
Reseated and checked.

Lspci doesn't find it. (It shows everything, including the onboard, but not the PCI-E card)

I guess I'll have to replace it somehow.

---

