---
title: "Can't get my Palm Z22 to sync with Evolution/j-pilot"
date: 2008-10-30
forum: Desktop Environments
---

### Post by inearlygaveup on 2008-10-30
I am still fairly new to Linux and have 8.04 Hardy Heron.
My problem is I can't get my Palm Z22 to sync with Evolution/j-pilot after research I think I am missing the vistor module as outlined in the posts below.

My question is how do I input the two instructions.


POST 1
Re: j-pilot problems in Feisty
Evidently the visor module is not being loaded automatically in feisty. 

1 - Type "sudo modprobe visor" and then try to sync. It should work at that point.  

2 - You can edit the /etc/modules file and add visor to the list to load it at boot.

Martin

---

### Post by jlavezzo on 2008-11-07
I've just upgraded to 8.10 AND just bought a Palm Z22 to replace a Sony Clie PEG something. The Sony never worked with gpilot (something about needing to be compiled into gpilot).  At least that's what I accepted.  The Clie had problems anyway.

So here I am with a new Palm Z22, visor module in my /etc/modules list, tailing /var/log/messags, watching the visor module attach a converter to both ttyUSB0 and ttyUSB1 BUT gpilot-control-applet still doesn't pick up that I've hit the hotsync button on my palm.

I have the timeout set to 2 as recommended in other posts. I've tried everything I can think of but I'm just not getting any useful feedback from gnome-pilot.

Here are some trimmed log messages:
> usb 2-1: new full speed USB device using uhci_hcd and address 34
> usb 2-1: configuration #1 chosen from 1 choice
> visor 2-1:1.0: Handspring Visor / Palm OS converter detected
> usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
> usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB1


Has anyone been successful in syncing a Palm Z22?

thanks

Jeff

---

### Post by plain_jim on 2008-11-11
My upgrade from Hardy to Intrepid was a disaster, so I had to do a clean install of Intrepid.  When I did, I had the same problem; neither jpilot (my choice) nor the gnome-pilot applet would sync with my Z22.  It turned out that I didn't have pilot-link installed; I had to get it (you can use the Synaptic Package Manager in "System", or you can use apt-get).

Then I had to do the stuff on **[this page](http://kaybyrd.com/?p=56)** (the previous two words are a link, although it doesn't show up well in my setup).  I use jpilot, so I did the stuff under "JPilot" and "Automatic Modprobe Visor".  (It sounds like you've already tried some of that stuff, but the page tells you exactly how to do it.  If you use jpilot, you won't have to monkey around with the gnome-pilot applet - and I didn't like Evolution; I had duplicate-entry weirdness.  But last time, after I did the stuff on the page to which I linked, gnome-pilot worked as well.)

As always, YMMV.

EDIT: One more thing:  my device is /dev/ttyUSB1, and my speed is 115200.

---

### Post by inearlygaveup on 2008-11-12
> **plain_jim said:**
> My upgrade from Hardy to Intrepid was a disaster, so I had to do a clean install of Intrepid.  When I did, I had the same problem; neither jpilot (my choice) nor the gnome-pilot applet would sync with my Z22.  It turned out that I didn't have pilot-link installed; I had to get it (you can use the Synaptic Package Manager in "System", or you can use apt-get).

Then I had to do the stuff on **[this page](http://kaybyrd.com/?p=56)** (the previous two words are a link, although it doesn't show up well in my setup).  I use jpilot, so I did the stuff under "JPilot" and "Automatic Modprobe Visor".  (It sounds like you've already tried some of that stuff, but the page tells you exactly how to do it.  If you use jpilot, you won't have to monkey around with the gnome-pilot applet - and I didn't like Evolution; I had duplicate-entry weirdness.  But last time, after I did the stuff on the page to which I linked, gnome-pilot worked as well.)

As always, YMMV.

EDIT: One more thing:  my device is /dev/ttyUSB1, and my speed is 115200.

Thanks plain_jim - when I get some time I will have another go

---

### Post by stoobers on 2010-01-19
After an upgrade to karmic koala (kubuntu) jpilot won't work for me.

Here is what I did to make it go.  It now works for me with the z22.

do the following:
sudo modprobe visor  (this gets the kernel going)

Now comes the magic.
start: jpilot
file: preferences: settings: serial port: other: /dev/ttyUSB? (now we find the ?)

plug in palm and put in hotsync "connecting with the desktop using cradle/cable" mode.
in a shell:
dir /dev/pilot
it will have CURRENT usb number.  This will change with EVERY hotsync and needs to be changed in the settings (this gives us the ? for the settings above.)
pick that /dev/ttyUSB? from the list, click ok, then click the hotsync on the main screen.

Shazam!  It worked!
My theory is jpilot gets some kind of stale ttyUSB thing from /dev/pilot.  Sounds like a bug.

---

