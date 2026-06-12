---
title: "Window Docks"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by Yes on 2007-08-29
I think that's what they're called.  The docks like Kiba and AWN.

Anyway, I just installed Kiba, and I have a question:  Is there any way to make it only show up on my desktop?  Otherwise, when I maximize the window I have open, it leaves space for the Kiba dock at the bottom of my screen.  Since the dock isn't all that wide, I end up having a strip of empty space covering 4/5's of the width of my screen below all my windows.  I really hate how this looks, but I love how Kiba looks on my desktop.

Thanks.

---

### Post by Inxsible on 2007-08-29
I think if you use the auto hide option of kiba, then once the dock hides, the windows become larger. Maybe that would work for you.

---

### Post by Yes on 2007-08-29
Nope, that doesn't work.  Thank's though.

If I can't do it in Kiba, does anyone know of any other window dock program that I can do it in?

---

### Post by PurposeOfReason on 2007-08-29
AWN has an autohide function.And if you read their forums, they're working on making it stay behind windows.

---

### Post by reacocard on 2007-08-29
You can do it in AWN. Open gconf-editor, navigate to apps -> avant-window-navigator and uncheck panel_mode. Restart AWN, and it will no longer reserve any screen space for itself.

---

### Post by Inxsible on 2007-08-29
> **reacocard said:**
> You can do it in AWN. Open gconf-editor, navigate to apps -> avant-window-navigator and uncheck panel_mode. Restart AWN, and it will no longer reserve any screen space for itself.
That in itself is enough to convince me to move from Kiba to AWN. 

Mini Project for tonight after a couple of beers ;)

---

### Post by Yes on 2007-08-29
Great, I installed AWN and it works almost perfectly!  I say almost because I still have one (sort of two) problem: I can't figure out how to add a launcher to another hard drive that's connected to my computer.  Is there any way to do this?  

My other closely related problem is that I need to delete the current launcher I have on my desktop that goes to my other hard drive.  Is there any way to do this?  It's not listed under "Desktop", and it isn't an icon.  Is there anyway to delete the hard drive launcher from my desktop?

Thanks!

---

### Post by reacocard on 2007-08-31
> **Yes said:**
> Great, I installed AWN and it works almost perfectly!  I say almost because I still have one (sort of two) problem: I can't figure out how to add a launcher to another hard drive that's connected to my computer.  Is there any way to do this?  

My other closely related problem is that I need to delete the current launcher I have on my desktop that goes to my other hard drive.  Is there any way to do this?  It's not listed under "Desktop", and it isn't an icon.  Is there anyway to delete the hard drive launcher from my desktop?

Thanks!

For the first, can can make a launcher with a command like 'nautilus /media/<drive>' replacing <drive> with the appropriate path to the drive. For the second, there should be an option for it in in gconf-editor under apps->nautilus->desktop.

---

### Post by Yes on 2007-08-31
That worked perfectly!  Thank you =D

---

### Post by Yes on 2007-09-05
Just a quick question, how do you eject things like flash drives if their icon isn't on the desktop?

---

### Post by reacocard on 2007-09-05
> **Yes said:**
> Just a quick question, how do you eject things like flash drives if their icon isn't on the desktop?

Go to computer in nautilus, or do

```
sudo eject /dev/<device>
```

where <device> is that device, eg sdb1.

---

