---
title: "[SOLVED] Need Help With AWN!!"
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by Fraser from Scotland on 2008-01-17
Please help! I have been trying to configure AWN for days but it just refuses to do what I want it to do! :( All I want it to do is be a program launcher, but I want custom icons for them (like the firefox ones) but I have no idea how to do any of this. When I click change icon it just makes the new icon really small, please help!!

---

### Post by Fraser from Scotland on 2008-01-17
ARGHH!! Please Help!! I'm begging! If unclear here is what I am asking:
1. How do I make AWN to be just a program launcher?
2. How do I apply the custom icons?

---

### Post by rune0077 on 2008-01-17
> **Fraser from Scotland said:**
> 
1. How do I make AWN to be just a program launcher?


You can't. AWN is both a launcher and a taskbar manager, and you can't have one without the other, sorry. I suppose you could write an applet yourself that handled just the launchers, but I can't help you there.

> **Fraser from Scotland said:**
> 
2. How do I apply the custom icons?

The change icon ought to work. If it doesn't, then try this: open your home-directory, enable hidden files, then go to /.config/awn/launchers. Here are all your launchers - right click on of them, select properties, click on the icon in the window that opens, then change it to something new. That should work.

---

### Post by Fraser from Scotland on 2008-01-17
ok thats great :) its good to know i cant have both :D I've tried changing the icons before but they just appear really small, is there any way of adjusting the size?

---

### Post by rune0077 on 2008-01-17
Did you try doing it with the second way I mentioned? And, is it just the icons you've changed that are really small, or is it all the icons? 

If it's just the icons you've changed, then maybe (just guessing here) you just picked some really small icons - be sure to check the size of the png of the new icon.

---

### Post by Fraser from Scotland on 2008-01-17
Ok, I'll try the second way, do you know how big they should be? The icons I mean.

---

### Post by rune0077 on 2008-01-17
Depends on what size you want them to be :) Somewhere in AWN-manager you can set the size of the actual bar, which will also determine the maximum size of the icons. I always just pick some that are larger than that (128x128) and then AWN scales them down to max size.

---

### Post by Fraser from Scotland on 2008-01-17
I used a 256x256 icon for firefox that I downloaded but it still shows up quite small, out of proportion to my other icons.

---

### Post by Tristam Green on 2008-01-17
It looks fine to me?  I don't quite understand.

---

### Post by Fraser from Scotland on 2008-01-17
Yeah i think it is fine, its just the other icons are bigger and arent from the same pack.
Thanks for oyur help Rune.

---

### Post by rune0077 on 2008-01-17
Okay, just try to open awn-manager (System > Preferences > awn manager), then go to the one that says "Bar appearances" and increase the bar height. This will also change the size of the icons.

---

### Post by Victormd on 2008-01-29
Quick question, kind of related... I'm trying to add Firefox to AWN so I added it as a launcher but the icon doesn't show up... Is there another way of adding applications that are not applets?
Strike that... I got it... dumb question... :)

---

