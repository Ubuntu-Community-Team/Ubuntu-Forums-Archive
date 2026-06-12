---
title: "Nautilus Background Bug"
date: 2008-05-15
forum: Desktop Environments
---

### Post by XFocus on 2008-05-15
Since the upgrade to Hardy I've had an issue with my nautilus background.  While the background image is large (1280x1024), the window will only show what is initially drawn.  In other words, if I stretch open the window or scroll down, the rest of the image isn't shown.  Instead I'm confronted by blank space (usually black/white). 

Is there a workaround/fix for this?  See the attached images

---

### Post by BlueSkyNIS on 2008-05-15
That's nothing, look at my screenshots :)

This happens when I change view mode to "View as List" and then change back to "View as Icons"

---

### Post by XFocus on 2008-05-15
> **BlueSkyNIS said:**
> That's nothing, look at my screenshots :)


Haha, that's awesome!  There has to be some sort of fix out for this by now.  I've been waiting patiently since Hardy was released :(

---

### Post by Awalton on 2008-05-15
We have no idea on this one, but we know that it's common to Intel hardware, so it's probably a bug in the way that we're using X somewhere down the line (else it's a driver bug and there's nothing we can do anyways).

The bug actually appeared in a piece of software that draws backgrounds on the canvas, which recently changed from being Eel to being some component in Libgnome. The change was done to land a patch from Fedora/Red Hat that allows users to have "Slideshow" desktop wallpapers through the addition of an XML file. We've tried for a couple of months to get the actual developer of that piece of software to comment on the change, but he seems unreachable (or just really, really busy, as Free Software developers tend to be)...

Anyways, sorry for the inconvenience, you can track the progress of the bug by going here and adding yourself to the CC list: [http://bugzilla.gnome.org/show_bug.cgi?id=492529](http://bugzilla.gnome.org/show_bug.cgi?id=492529)

---

### Post by XFocus on 2008-05-15
Thanks for the info.  Unfortunately I'm running an AMD machine.  Not sure if it's Intel specific or not.  Hopefully a fix gets released soon  :-)

---

### Post by Awalton on 2008-05-15
> **XFocus said:**
> Thanks for the info.  Unfortunately I'm running an AMD machine.  Not sure if it's Intel specific or not.  Hopefully a fix gets released soon  :-)

What I meant is that people who have reported it have commonly had Intel video cards, but it's still probably a problem in the way we're using X somewhere (and there's still a chance it's a video driver issue).

Stuff that far down the stack is pretty opaque to me, so I have no idea what the issue could be. We really need Soren or another X-expert to take a look...

---

### Post by larryfroot on 2008-07-07
Hi, am experiencing the layout of my (wallpaper) nautilus backgrounds going wrong. I checked out and tracked the bug report which seems to have been fixed (thanks for the link to bugzilla, by the way!)

What actually happens now? Is the patch due to be implemented in intrepid? Or will an update of nautilus include it? What happens to patches when they materialise? Is there really a cli fairy? Be nice to know and with pleasure anticipate the return of a large part of the eye candy back to the desktop. Where it belongs. 

Thank you for your time!

---

### Post by BlueSkyNIS on 2008-07-07
Heeey! I checked again to set a background picture and now it works! I have proposed updates enabled and have no idea which update fixed it. :popcorn:

---

### Post by larryfroot on 2008-07-07
Nice one mate! I set up proposed updates and downloaded them, but sadly wallpaper + nautilus background still doesn't work properly for me! Might try a reboot tho'. well, you never know. But thanks for popping up and letting us know of developments, very good of you!

---

### Post by hpis2cool on 2008-10-23
Same bug as the first description...It's very annoying and my Hardy is completely updated. Using an Intel desktop.

---

### Post by BlueSkyNIS on 2008-10-23
I have read somewhere that Nautilus doesn't work nice with pictures bigger than 400 pixels. Can you try a smaller background?

---

### Post by SamNSane on 2008-10-23
This is interesting. I didn't even know about this feature of Nautilus.

I have an nVidia video subsystem running the restricted drivers. When I drag a pattern or color from the selector to a Nautilus frame nothing happens.

This is Hardy, completely updated as of this morning.

---

