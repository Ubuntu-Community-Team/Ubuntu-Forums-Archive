---
title: "I'm almost afraid to ask what I just did..."
date: 2009-04-21
forum: General Help
---

### Post by DeadIrishD on 2009-04-21
I tried messing around with the resolution of the screen, to make it smaller, well I made it a lot bigger, and am now unable to even scroll down to change the settings back, to where it was before, to make matters worse the screen keeps on flashing, and there is a window that states "Unknown"

any suggestions, or did I just pretty much mess everything up?

Another thing, that I had tried was to reinstall, Ubunto, however the disc will now not be read, or something...

---

### Post by iponeverything on 2009-04-21
boot into rescue mode (on the grub menu) and choose xfix

---

### Post by blazemore on 2009-04-21
Press Ctrl+ Alt+ F1 to get to a terminal.
Log in with your usual username and password
Run the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

EDIT: Or Fix X server, forgot about that.

---

### Post by DeadIrishD on 2009-04-21
I'm confused, as to how I would be able to boot into the rescue mode.

I tried to see if it was in options on the sign in page, but all I got for options were,

Last Session
1.) Run Xclient script
2.) Gnome
3.) Secure Remote Connection

Failsafe Gnome
Failsafe terminal

Perhaps, there is something that I am unable to see, or perhaps their might be different versions of Ubuntu out there, if that would make a difference, the version I have is 8.10 Desktop Edition, and all up to date on, the upgrades, not counting my video card for some odd reason.
---------------------------------------------------------------------------------------------------------------------------------------------------------

Not sure on the rules as far as making a new post goes, for the same thread or not but I was able to find Xfix, but even that did not help me out at all.

---

### Post by coffeecat on 2009-04-21
It sounds as though you only have Ubuntu on that machine and are not seeing the Grub menu.

Start to boot up and just after the POST screen you should see a message 'Press ESC for grub...' (or something like that - I'm going from memory). Don't blink - it only lasts a second or so. Press ESC and the grub menu should appear. Now choose rescue mode which will boot you up into a non-GUI console where you can do xfix

By the way, the 'Unknown' window was probably a message from your monitor, not from Ubuntu.

---

### Post by DeadIrishD on 2009-04-22
I managed to fix it, by reinstalling it, so feel free to close this thread, I'd like to say Thank-You for all of the help. :)

---

