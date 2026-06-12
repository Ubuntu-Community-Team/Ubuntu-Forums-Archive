---
title: "Another X360 Controller issue..."
date: 2013-11-24
forum: Gaming &amp; Leisure
---

### Post by MrMichaelHill on 2013-11-24
So, this morning I was having a play with PCSX, got Final Fantasy 7 running, decided to try and connect my xbox controller to see what would happen, straight away it lit up the top left portion of the green ring (Player 1) and PCSX picked it up as an xbox controller! and in game it worked pefectly!

Booted my PC up this evening and got greeted by a terminal log in! Some graphics driver failure... Fast forward an hour and I've re-installed my OS! (12.04 64bit) Wanted to play TF2 with my xbox controller just now and when I plug it in the light doesn't come on the controller for about 5-8 seconds and then the whole green ring just flashes, I've been googling for a little bit now and tried numerous 'fixes' jstest, disabling xpad etc...

I have no idea why it just worked on my previous OS install and now it won't! :( I have installed all updates available too!

Any help at all would be great thanks!

---

### Post by DanglingPointer on 2013-11-24
Hmmm... do other USB devices work?  try plugging in a USB drive or a anything USB known to work with Linux.  See if they work.

---

### Post by MikeCyber on 2013-11-25
yes unplug other usb devices helped me with Metro LL

---

### Post by MrMichaelHill on 2013-11-25
Right, I unplugged my Saitek Eclipse 2 keyboard, plugged the controller in and it worked!

Although I've not tested it in game the xbox controller is showing the player 1 light lit up and jstest-gtk is showing it correctly and showing all the axis working properly :)

Of course I plugged my keyboard back in and its working now!

Funny note! If you un plug the controller then plug it back in you become player 2 on the xbox controller, then 3 or 4 if you do it again!

I'll mark this as solved and will report back some more details when I test in game later :)

Thanks!

---

### Post by MrMichaelHill on 2013-11-25
Reporting back!


Team Fortress 2 worked like a charm! All buttons premapped and it even has a slightly different weapon selection menu when your using the gamepad! Gaming on Ubuntu is become absolutely fantastic!

---

### Post by dannyboy79 on 2013-11-25
so the only thing you had to do was unplug your Saitek Eclipse 2 keyboard, plugg in the controller in and it worked? that's just weird. weird you were presented with a graphics issue to begin with and couldn't solve it without doing a completely new installation. for this exact reason I would strongly suggest using clonezilla to create an image file of your /   partition. especially just prior ro making major system changes. Good luck

---

