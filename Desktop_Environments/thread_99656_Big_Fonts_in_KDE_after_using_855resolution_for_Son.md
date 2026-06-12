---
title: "Big Fonts in KDE after using 855resolution for SonyTR2 widescreen"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Crowhurst on 2005-12-06
I used 855resolution to get the 1280x768 resolution to work on my TR2 running ubuntu 5.10 and KDE upgrade.

I added a script to /etc/rc2.d to create the 1280x768 resolution.
Then when X started it found the 1280x768.

HOWEVER
I noticed the fonts of my type in the login screen was very large. However, Gnome worked fine.

Then when I went to KDE, the fonts/title bar and everything is huge.

I noticed my screen dpi is 141, this is registering just fine. But the fonts are designed for 100 it seems because that is what is called in the beginning. But this would make the fonts smaller, not larger.

Any ideas?

Thanks in advance!

---

### Post by rudiz on 2005-12-06
right beside the K-startbutton there is an icon.( depicting a computer)..click it...them choose settings>display>fonts...there u can change the font size

---

### Post by Crowhurst on 2005-12-06
I should have been more clear. I have finally hacked (not fixed) the problem.

It is not just the fonts, but everything that was too big. So when i change the font size it only changes some of the fonts. then the fonts in websites become erratic with some of them very large.

I checked and found that i had dpi calculated (correctly) at 141x141. I went into xorg.conf and modified my display size so that the 1280x768 would equal 100dpi (i changed the display size to 324x194) in xorg.conf.

This had the desired effect. I have not yet checked it in gnome which used to work fine. While my dpi is 141 technically, i dont know why i cant adjust the desktop design to utilize that dpi.

---

### Post by dto on 2005-12-09
I just installed KDE on my Ubuntu Breezy laptop (running at 1680x1050) and I'm seeing the same thing with the fonts. 

I've set all my fonts to a smaller size, but that still leaves me with two problems. If I do something that requires me to enter a password for root access via the GUI, then the fonts are huge again for that task after I enter the password. Also, Firefox applicaton fonts (i.e., the menus in FF) are tiny, while in Thunderbird they are still  pretty large. 

I would think that changing the DPI setting would help me out, but I can't find it in KDE. In Gnome, it's right there in the fonts settings. Any idea where it is in KDE?

---

### Post by dto on 2005-12-09
Fixed!

In /etc/kde3/kdm/kdmrc I changed:
```
ServerArgsLocal=-nolisten tcp
```
to
```
ServerArgsLocal=-nolisten tcp -dpi 96
```
Now all my fonts appear to be much more uniformly sized, and not huge. :)

---

### Post by linhgb on 2005-12-18
Thanks dto! I've been searching for a solution to this and yours works beautifully. Strangely I had no such problem before with my 1680x1050 laptop, until tonight when I hooked a 1920x1200 external screen to it. After configuring xorg.conf, the fonts look huge and were flowing out of the windows etc. Thanks again.

---

