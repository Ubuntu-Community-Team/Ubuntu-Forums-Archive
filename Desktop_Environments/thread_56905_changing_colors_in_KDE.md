---
title: "changing colors in KDE"
date: 2005-08-14
forum: Desktop Environments
---

### Post by floyd27 on 2005-08-14
HI.
i was able to figure out most little things i wanted to get KDE to look right.
I however cant find a way to change the color of the top header task bar...
You know the one that has min/max/close....
I changed it from the default style but cant get a color change. 
anyone knwo the solution?
thanx

---

### Post by SGC on 2005-08-14
To change the color scheme:
Control center -> Appearance & themes -> Colors

If you like your color scheme, and only want to change the title bar, then locate your currant scheme from here and open it with a text editor (kate, kwrite, ...):
~/.kde/share/apps/kdisplay/color-schemes

And change the line:
activeBackground=R,G,B

where R, G, and B are the value of red, green, and blue respectively. You can use KColorChooser from (kmenu -> graphics -> more applications) to help you in knowing these values.

---

