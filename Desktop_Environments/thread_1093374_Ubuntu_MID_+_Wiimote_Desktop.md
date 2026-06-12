---
title: "Ubuntu MID + Wiimote Desktop"
date: 2009-03-11
forum: Desktop Environments
---

### Post by roblloyd on 2009-03-11
I'm interested in integrating the use of a Wiimote with Ubuntu. 

My main computer runs Ubuntu 8.10 with Gnome. I have a Wiimote that I Use as a mouse from across the room. Its good, but it could be great. Imagine a "Wiibuntu" media centre.

I have seen the ubuntu netbook remix and ubuntu MID, but these packages are intended for tiny computers, they have troubles if you try and use them on normal PC hardware. E.g. Netbook remix doesn't like compiz, MID only works on atom processors.

Does anyone have any Ideas of how to INTEGRATE a Wiimote with the Ubuntu desktop? This is a fairly open question, I know. Hopefully the open source community can show what can be done with a little bit of desire and a nice bit of technology.

Post your thoughts!

Rob

---

### Post by crysys on 2009-03-13
I like the idea and want to do something similar with my old hardware when I upgrade.  I think something like the MID interface would easily double as a 10 foot UI for media pc use.  I didn't know MID only ran on Atom processors, that's too bad.

---

### Post by roblloyd on 2009-03-13
My thoughts exactly. I think the best solution would be the big dumb buttons approach. I've Got my system working in a round about way already. It uses maximus (from the ubuntu netbook repositories) to make all windows work in full screen. Then I use slightly tweaked gnome panels to have launcher and gnome panels hidden away while working with programs. 

One thing i've found is that you can stop elisa from going into fullscreen mode automatically by changing the config file. It's pretty obvious how to do it. 

Here's a quick screenshot. All of the panels are set to autohide

---

### Post by crysys on 2009-03-15
Check out Jaunty Netbook Remix.  The alpha ran from a usb stick on my laptop just fine.  I'm going to wait for a release candidate before I start messing with it but it looks promising.  I think that enlarging the main panel will give you the big icons you want.

Have you noticed that elisa can play .iso files?  But for me it can't scan forward or back in the movie.  It scans ok in regular media.  except for this issue, I like it a lot.

---

### Post by roblloyd on 2009-03-15
jaunty netbook remix eh... hopefully they've sorted out the compiz issue. i'm also trying to get hold of the customised gui's that you get with netbooks. I know of the HP 'Mi' interface and i know dell and acer have their own. The trouble is finding the packages so i can try them out on a big screen.

on the elisa front, im glad the application is coming along, now i just hope they get the plugins working, im running 64 bit, that might have something to do with it.

now, where the hell are those gui packages....

crysys, have you tried connecting a wiimote yet?

---

### Post by crysys on 2009-03-15
I haven't even bought a Wiimote yet.  I want to get everything else together first because without a media center to use it on it will just collect dust in a drawer.  Then the final purchase will be a new 40" tv and building a swing arm to mount it in front of the desk and swing it over to point at the living room couches.

As for the HP interface, look up the thread detailing using the HP mini theme, that should get you a link to HPs package repository.  Then it's a matter of digging out the right packages.

Yea, I'm still using 32bit, as is the remix image.  I hope 64bit will be up to par in a release or two.  I'll need the memory addressing at that point.

---

### Post by roblloyd on 2009-03-19
So, as is always the way when you have something important to do, I've been playing with this wiimote idea a bit more. 

I found that ubuntu mid edition is a bit of a no go because it only compiles for lipa architecture. but the window manager for MID is called hildon. there is a package in the repositories called hildon-desktop then you just have to make a gdm-session entry

[http://ubuntuforums.org/showthread.php?t=582867](http://ubuntuforums.org/showthread.php?t=582867)

this gives you the desktop that can be seen in the attached screenshot. Not much works except for the clock and the keyboard. Where to go next is something i need to ponder

If anyone has any Ideas, let me know

EDIT; I got a bit further and now at least have a theme installed for hildon desktop! Now to get the menus in there! which files do i need to fiddle with?

---

### Post by t3tech on 2009-04-20
The MID interface will work as you've discovered. I'm playing with a jaunty netbook-remix/MID build and working on creating a clutter interface sorta like moblin-clutter-home. For now I have compiled the old moblin-clutter-home to work on jaunty with clutter 0.8 or 0.9, don't remember which right now - that was fun. :biggrin:

Right now off the top of my head I can't remember if I started with MID or NBR as my base but I think it was an NBR image. As I recall, I removed the NBR packages and installed the MID packages. Anyway I have it running the MID desktop interface and can start the moblin-clutter-home I compiled. Currently that runs in Virtualbox and I have it stripped down to a CD size iso. I just need to figure out which files determine the desktop so the clutter interface is the default.

I'll see if I can figure out what it was I did and get a package manifest list if it would help.

---

### Post by hesjnet on 2009-04-20
You might want to check out [Johnny Chung Lees projectpage]("http://johnnylee.net/projects/wii/")

---

### Post by t3tech on 2009-04-27
Just in case this info is helpful the place to start looking for the desktop startup config files is /etc/X11/Xsession.d/

For some more details specific to Ubuntu MID:
[https://wiki.kubuntu.org/MobileAndEmbedded/MIDStartupGutsy](https://wiki.kubuntu.org/MobileAndEmbedded/MIDStartupGutsy)

---

