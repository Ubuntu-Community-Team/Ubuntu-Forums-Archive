---
title: "Hardware detection on boot?"
date: 2005-05-06
forum: Desktop Environments
---

### Post by dlanor78 on 2005-05-06
I lug my pc around a lot these days, and usually I just take the tower and use other ppls mouse, keyboard, and monitor.  When I'm using windows this is no problem, but in kubuntu, I had a problem with the mouse.

Is there a way to get kubuntu to do a knoppix style hardware detection on boot to get around this?  My only other alternative as far as I can figure is to create machine specific xorg.conf files, and when x fails to boot do something like "mv xorg.conf xorg.conf.homepc" then mv xorg.conf.differentpc xorg.conf".  Does that make any sense?

Anyway, thanks in advance for any advice.

---

### Post by crazybill on 2005-05-07
What kind of mouse are you having trouble with?

---

### Post by dlanor78 on 2005-05-07
The kind of mouse I use at home is a GE 97769 Deluxe Optical mouse.  This mouse has 2 scroll wheels (one clickable), back and forward buttons, and regular left and right buttons.  To get it working properly in linux I need to have the following in xorg.conf:

```

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "Protocol" "evdev"
	Option "Dev Name" "A4Tech USB Optical Mouse" # cat /proc/bus/input/devices
	Option "Dev Phys" "usb-0000:00:03.1-1/input0" # cat /proc/bus/input/devices
	Option "Device" "/dev/input/event4"
	Option "Buttons" "9"
	Option "ZAxisMapping" "4 5"
EndSection

```

Most mice I use when I take my pc places is just a standard 2 button scroll mouse, which of course uses something like IMPS/2 and won't work at all with evdev (or so it seems).  Last time I ran into this I had to edit the xorg.conf file with nano so I could start X.

I don't specifially remember any other major problems, except maybe the resolution on a different monitor was a bit weird.  That one was no biggie though :)

---

### Post by johnprgr on 2005-05-07
Perhaps you can make an entry for a secondary mouse in your xorg.conf, "CorePointer" would be you main mouse and "OtherPeoplesMice" your uknown generic mouse, then use Option "SendCoreEvents" from OtherPeoplesMice to CorePointer during operation.

I don't know if it would work, but maybe point you in an interesting direction to investigate.  Your post sounded like you know your way around and xorg.conf file.

Hope this helps in some way

---

### Post by dlanor78 on 2005-05-13
Sorry, I haven't been home this last week.  That sounds like an interesing idea johnprgr.  I may give that a try.  I would like to ultimately have the hardware detection though so I can also slap the hard drive in another pc sometimes.  Or even install to an external hard drive that I can  hook up to other pcs.

Guess for that I'll just use knoppix for now :)

---

### Post by fredbird67 on 2008-02-14
DLanor78, it's funny you should mention the GE 97769 mouse, because my wife got me one of those for Valentine's Day, and I opened it this morning before coming to work (I have the afternoon and evening shift today) and tested it on my computer, running Linux Mint Xfce edition.  I'm happy to say that all the basic mouse functions work just fine by default, and thanks for posting the instructions to get those other buttons and that other scroll wheel working! :)

I had mentioned to my wife a few days ago that I could use a new mouse because while my Kensington mouse was still working perfectly, the rubber insert on the side of it where I rest my thumb was coming loose, and in fact, it had started doing so just a few months after I bought it back in 2005, but lately, it had been REALLY bugging me no end.

Fred in St. Louis, MO USA

---

