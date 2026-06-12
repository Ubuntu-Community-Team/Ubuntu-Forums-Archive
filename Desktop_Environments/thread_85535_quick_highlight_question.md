---
title: "quick highlight question"
date: 2005-11-02
forum: Desktop Environments
---

### Post by nrwilk on 2005-11-02
This isn't any sort of a big deal at all, but I'm curious.

When I drag a bounding box around some icons on the desktop to highlight them, it seems to lag a whole lot.  The more complex the background behind the bounding box is, the slower the action goes.  It's *almost* unnoticeable when the background is solid, but it still seems a bit laggy.  It's even slow when dragging the bounding box around no icons, just background.

So,
Is this normal? Is it a KDE thing, or an X11 thing?  Is there any way to speed it up?

Why does it happen even though my machine is moderately graphics capable?
(I get ~3900-4000 fps in GearsGL)

I just think this is pretty interesting, and it would be nice to get a smooth box drawn to highlight on the desktop, but it isn't that big of a deal.

Thanks!

---

### Post by HermanAB on 2005-11-02
Hmmm???  Just press the Ctrl key and click the icons or whatever you want to highlight.

---

### Post by nrwilk on 2005-11-03
[QUOTE=HermanAB]Hmmm???  Just press the Ctrl key and click the icons or whatever you want to highlight.[/QUOTE]


Actually, the question is more about aesthetics than a call for a better way to highlight multiple items.

I'm interested in how the graphic part of KDE works.  Or, would this be a property of X11?

It doesn't matter all that much in reality, I know other ways to highlight, such as the one you have suggested.  I was just wondering if it's only me, or it's the normal behavior.  And why it happens even though the box is capable of doing it much nicer.

That's all.

---

### Post by nrwilk on 2005-11-09
Anyone?  I'm curious about this...

---

### Post by nrwilk on 2006-01-23
I was just browsing, and I happened to read a thread which contained a complete answer to this problem.  tseliot, who wrote those awesome nvidia driver howto threads we all use, casually mentioned this fix (which worked for me completely):

The quote comes from this thread: [http://ubuntuforums.org/showthread.php?t=116421](http://ubuntuforums.org/showthread.php?t=116421)

[QUOTE=tseliot]
If you have an nvidia graphic card you have to install the proprietary drivers.

Then:
Code:

sudo gedit /etc/X11/xorg.conf

OR
Code:

sudo kate /etc/X11/xorg.conf (if you use KDE)


And add the following option at the end of the Section "Device":
Code:

Option "RenderAccel" "True"


Then log out, press CTRL+ALT+Backspace (so as to restart the xserver)

Enjoy!

OR if you do not have an nvidia card or the drivers do not work for you, there is a way to disable that effect (which most distros don't use) but I can't remember it since I'm mainly a GNOME user[/QUOTE]

Just thought I'd post it in case anyone else found this annoying.

---

