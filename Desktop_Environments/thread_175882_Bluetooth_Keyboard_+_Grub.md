---
title: "Bluetooth Keyboard + Grub"
date: 2006-05-14
forum: Desktop Environments
---

### Post by Roger Mudd on 2006-05-14
Hello All,

Just a quick question about Bluetooth keyboards and GRUB. I'm currently running a dual-boot system (Breezy/XP) and I'm trying to iron out all the kinks. One of those kinks is my inability to use the Bluetooth keyboard to select options in GRUB. What's strange is the fact that I can use the keyboard to get into my BIOS and make alterations before GRUB loads. Unfortunately, once in GRUB, I'm powerless. Anybody have any ideas?

BTW - The keyboard is a Logitech MX 5000 combo and the motherboard is an ABIT IC7-G.

---

### Post by Mygly on 2006-05-21
Try going into BIOS and looking for an *enable USB keyboard/legacy support* option or something that is worded similarly. I had the same problem but with my wired USB keyboard and this fixed it. Hope this helps.

---

### Post by mally42 on 2006-07-10
I have the same problem.  I have USB legacy support enabled in my BIOS.

---

### Post by Endolith on 2007-09-27
My bluetooth keyboard works without any configuration in the BIOS (because I can bring up the BIOS config by pressing F2), in grub, and in GNOME.  It did not work on another computer, though, so I'm wondering if this is because I paired the keyboard and bluetooth adapter in Windows before rebooting into grub.

---

### Post by digital_exhaust on 2007-09-27
That's odd... I have a DiNovo Edge, connected via a dongle and I have had no problems at all... In fact, I just got this board a few weeks ago, disconnected my usb board, plugged the dongle in and all has been fine since, I didn't have to change a thing... 

Not much help, just thought I'd share my experience.....

---

### Post by Endolith on 2007-09-27
Mine's a Rocketfish keyboard and mouse combo.

I first tried it on my laptop running Ubuntu, and can see it with ```
hcitool scan
```, but doesn't work and I'd apparently have to do a bunch of command line stuff to make it work.

So I booted my desktop into Windows and plugged in the included Bluetooth dongle  (laptop has a built-in card).  It installed the dongle drivers, and then I was able to see the keyboard and mouse in the Bluetooth devices thing.  I added both and used the passkey from the documentation.  Then both started to work.  So then I rebooted, and the keyboard worked in grub and the GNOME login screen with no configuration.  I was quite surprised, but happy.   :-)

---

### Post by jacob.schoen on 2007-09-28
Endolith,
Just out of curiosity, does your scroll wheel work on your rocket fish mouse. I also have a blue  tooth rocket fish mouse and keyboard and they work well, except for the extras buttons on the mouse and specifically the scroll wheel. 
If you have this working on yours, I would be interested in knowing the steps. I have been looking for a solution and found some information about edition my Xorg.conf file if I remember correctly, but I already had the line they said to add. 

So I am at a loss. If anyone knows I would be grateful for assistance.

---

### Post by Endolith on 2007-09-28
> **jacob.schoen said:**
> Endolith,
Just out of curiosity, does your scroll wheel work on your rocket fish mouse. I also have a blue  tooth rocket fish mouse and keyboard and they work well, except for the extras buttons on the mouse and specifically the scroll wheel. 
Nope.  I hadn't tried it, but neither the scroll wheel or any of the multimedia buttons work.  Also the mouse is really jerky, almost intermittent.  I am mostly interested in the keyboard since I already have a non-Bluetooth wireless mouse that I love.
> I have been looking for a solution and found some information about edition my Xorg.conf file if I remember correctly, but I already had the line they said to add.
That's probably the key.  There are lots of guides online for getting stuff like that to work.  Often the keys *are* being picked up by the computer, but not "going where they're supposed to".  I remember struggling with this stuff a lot when I first tried Linux.  It's not fun.  :-)

---

### Post by BrooksOfSheffield on 2007-10-19
Using the rocketfish dongle, I could never get the extra buttons or the scrollwheel to work.  Lucky for me, I had another dongle that I plugged in...  snagged the MAC addresses for the keyboard and mouse from Windows...  and now everything automagically works.

---

### Post by Endolith on 2007-10-20
> **BrooksOfSheffield said:**
> Using the rocketfish dongle, I could never get the extra buttons or the scrollwheel to work.  Lucky for me, I had another dongle that I plugged in...  snagged the MAC addresses for the keyboard and mouse from Windows...  and now everything automagically works.

Interesting.  I'll have to try it on this laptop, which has a built-in Bluetooth card.

---

