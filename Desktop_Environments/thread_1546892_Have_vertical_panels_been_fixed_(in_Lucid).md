---
title: "Have vertical panels been fixed? (in Lucid)"
date: 2010-08-06
forum: Desktop Environments
---

### Post by outofsync on 2010-08-06
I tried the Lucid live CD when it was released, and I found that the GNOME panels were unusable when set in vertical orientation (there were aesthetic glitches, but also functional glitches because for example the power off button was missing). I searched for it, and found that other people were aware of these bugs.

I use Intrepid, and vertical panels work. I prefer not to upgrade to Lucid until vertical panels are usable, because I need them (because of the widescreen aspect ratio of my laptop).

So, the question: Have the vertical panels been fixed in the latest Lucid updates? Are they usable now?

Thanks a lot!!

---

### Post by JonasDK on 2010-08-06
I use Lucid and tried putting up a vertical panel and I don't see any problem. You can add a shutdown button via 'Add to Panel...' The only thing I couldn't live with is that the text from the menu is turned by 90° (the words Applications Places System), so it is hard to read. But no graphical glitches over here. :)

I've experienced some fails in the Live CD too, while it was fine after actually installing it. I got the Live CD so far to give an error when I clicked on anything in the menu. A reboot with the Live CD fixed that.

Do you want to replace the horizontal panels completely with vertical ones? The window selectors are going to be hard to read while being 90°... :p

Greets,
Jonas

---

### Post by mcduck on 2010-08-06
Depends.

Some applets still don't work that well in vertical panels. I doubt they'll ever do that.

If by graphical glitches you mean the background image, that's something you can easily fix in the exactly same way it's done in every previous Ubuntu/Gnome version; by making sure your GTK theme doesn't try to set a panel backgrond image, then setting one yourself through the panel's options, and finally enabling background scaling/rotation through gconf-editor.

Seriously, though, I haven't noticed any difference in panel behavior between 10.04 and previous versions. (apart from one older release that had nasty bug with transparent background images.)

---

