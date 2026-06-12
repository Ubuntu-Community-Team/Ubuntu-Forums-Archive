---
title: "Getting Bluetooth to work"
date: 2007-06-17
forum: Dell  Ubuntu Support
---

### Post by giosetti on 2007-06-17
I have an Inspiron 640m (in US this is 1405E) data see below) on which I have installed Ubuntu 7.04 which works perfectly out of the box except for Bluetooth. 

Anyone knowing how to get this working?

---

### Post by kiddyfurby on 2007-06-17
why do u think its not working?

you will need the following package to get started:
gnome-bluetooth
bluez-gnome

---

### Post by giosetti on 2007-06-17
Yeah, works perfectly now with these packages. Thanks for the hint.

---

### Post by sr20ve on 2007-06-23
I've got both gnome-bluetooth and bluez-gnome packages installed along with some other BT packages I found and still can't get BT to work.

When I type hidd --search, it says searching... Then immediatley returns to the command prompt. It doesn't appear to be working.

Any suggestions?

I'm trying to add my BT mouse on an E1505 with the built in BT.

---

### Post by BluewookieJim on 2007-06-24
I'm running Ubuntu 7.04 on my almost 2 year old Dell i6000d notebook. I got bluetooth working without much hassle, but I have noticed one thing. 

When I connect my logitech v270 bluetooth mouse, it finds it right away and all, but the pointer has a slow-steady "crawl' going on, moving on it's own without me touching it.

It's not the surface that it is on, as I've tried it on mouse pads, on bare desk surface, etc.. I also use it without issue on my Win XP bootup. If anyone has any ideas, please share.

---

### Post by jppaynesr on 2007-06-24
The Dell Inspiron E1505 does not come standard with bluetooth, it is an option. This caught me too, since there is a bluetooth indicator above the keybord.
Here's how you can check. Turn off your computer. Turn it over and remove the battery. Inside the battery compartment next to the side of the laptop is a small door. Remove it. If there is a loose cable inside, you dont have bluetooth hardware installed.

---

### Post by sr20ve on 2007-06-26
> **jppaynesr said:**
> The Dell Inspiron E1505 does not come standard with bluetooth, it is an option. This caught me too, since there is a bluetooth indicator above the keybord.
Here's how you can check. Turn off your computer. Turn it over and remove the battery. Inside the battery compartment next to the side of the laptop is a small door. Remove it. If there is a loose cable inside, you dont have bluetooth hardware installed.

It does have the bluetooth option. I recently wiped vista off my laptop and my bluetooth worked fine.

Is there known issues with the integrated bluetooth on the E1505?

I connected a usb bluetooth dongle and that works fine, but It'd be nice if I could just use the internal.

---

