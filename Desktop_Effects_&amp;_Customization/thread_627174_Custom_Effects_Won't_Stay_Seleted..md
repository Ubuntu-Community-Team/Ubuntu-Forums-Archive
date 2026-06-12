---
title: "Custom Effects Won't Stay Seleted."
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by Scoobie_snack on 2007-11-29
Hey there,

I have a problem with Ubuntu Gutsy 7.10 and the custom desktop setting. I have spent 6 hours or so, reading other peoples messages to see if I can find a fix but I can't find a thread with the same problem as this. I'm only 2 days old in linux so I don't really know what I can do to sort this out.

I think I  have installed all the stuff I need and the restricted drivers for my ATI Mobility Radeon 9700.
I can select the custom option, play with the preferance settings, change the settings in Advance Desktop Effects Setings and set the options in GL Desktop but when I click close on the  , it doesn't stay selected. If I go back in there, the setting will say "Extras" and not :Custom"

I get no errors of any kind so I'm kinda stuck.
Any help you guys can give will be most welcome.

Thanks in advance,
Scoobie. :guitar:

---

### Post by WestCoastSuccess on 2007-11-30
I have the exact same problem - keeps reverting to "extra' - very frustrating!

I'm running an AMD X2 with NVidia 7600GS, Gutsy, 2GB and it's driving me nuts!

---

### Post by mozetti on 2007-11-30
I'm having a similar problem, in that every time I restart it reverts to "No Effects" and I have to select "Custom" using the "Appearance" menu. I'm only tagging on because hopefully it's the same cause.

Ubuntu Gutsy
Nvidia 6600-series card (forget the exact model) using the "Restricted Drivers" nvidia driver.

---

### Post by Scoobie_snack on 2007-11-30
It seems that I'm not alone lol
I've been looking through some free Linux books and online docs and I still can't seem to find out what the fix is... Its probably something so simple and one of the Uber Ubuntu wizards will come along and tell us to change a few settings and it will all work :lolflag:

---

### Post by rogeriovinhal on 2007-12-01
I have the same problem, and I think that the majority of the issues regarding compiz is actually this one.

From time to time, when I start my computer, some plugins that were checked become unchecked. The most common ones are: "Move Windows", "Put", "Window Decoration", "Window Preview", "Desktop Cube".

Non-deterministically these plugins revert from checked to unchecked, and then something of my desktop stops working. Needless to say that this bug is very annoying. I really hope they get it fixed, because it has been this way since I installed Gutsy.

Can anyone that knows how launchpad works see if there is any bug filed there for this? I am not familiar to launchpad...

---

### Post by john.nicholls on 2007-12-01
On the Compiz forums one of the first things to try is to go to CompizConfig Settings Manager, go to Preferences, and deselect "Enable Integration..."

---

