---
title: "Make Chromium look like FF4?"
date: 2011-03-13
forum: Desktop Environments
---

### Post by lancest on 2011-03-13
How to make theme Chromium like Firefox 4. (orange text selection)
I've not been able to figure that out completely.

I found Ambiance theming but no orange text selection in the address bar.

---

### Post by Krytarik on 2011-03-13
Check what is selected in Chromium's options:
"*wrench* -> Preferences -> Personal Stuff (tab) -> Appearance".

It seems like you have "Use Classic theme" selected there.

---

### Post by lancest on 2011-03-13
I've been able Chromium to match 10.10/11.04 Ambiance theme except that the text selection in the address bar ISN'T ORANGE. 
Firefox 4 nailed that.

---

### Post by Krytarik on 2011-03-13
I tested it with Maverick's version of Ambiance at my Lucid system, and it looks like it should, orange.

---

### Post by lancest on 2011-03-13
[This works]("https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp") from Google.
But the text selection is blue.

---

### Post by Krytarik on 2011-03-13
Sorry, but did you *really* check what I mentioned earlier!?

---

### Post by lancest on 2011-03-13
I have "use GTK theme" and "use system titlebar and borders" enabled there.
Always have. 

Thanks for trying. :) 

I guess what I need to know is if Chromium has been properly themed for Ambiance as FF 4 has?

I prefer Chromium by a mile and I'd rather it match up a bit better with Ubuntu Ambiance.
 
( I don't prefer the orange tab area but would rather have matching orange text selection included)
. 
Had this problem a while.
FF 4 woke me up - but it's a bit inferior in font rendering.

---

### Post by Krytarik on 2011-03-13
Sorry, I didn't immediately realize that you will have more than two choices in Chrome's Appearance options, now that you installed at least one additional theme.

I don't know why it is not working the same like at my system with "Use GTK+ theme" being selected.

As for the font rendering: That annoyed me also when I first tried FF4. I had blue "shadows" at some characters. But I figured that I need to disable "Subpixel" rendering in "System -> Preferences -> Appearance -> Fonts -> Details", since I'm using an old CRT. I have it at "Grayscale" now.

---

### Post by lancest on 2011-03-15
Figured this out (mostly).
From Google Chrome help:
Do this:  
gedit  /usr/share/themes/Ambiance/gtk-2.0/apps/chromium.rc

Paste this in towards the bottom:

 style "chrome-gtk-frame"
{
    ChromeGtkFrame::frame-color = "#3c3b37"
    ChromeGtkFrame::inactive-frame-color = "#3c3b37"

    ChromeGtkFrame::frame-gradient-size = 0
    ChromeGtkFrame::frame-gradient-color = "#5c5b56"


}

class "ChromeGtkFrame" style "chrome-gtk-frame"

As far as I know this is the present state of Chromium- Ambiance integration into Ubuntu (if you want to get rid of the orange tab area and still have orange text selection in the address bar.) 
Chromium is just better for me, and I like it matching Ubuntu.

---

### Post by Krytarik on 2011-03-15
Thanks for reporting back, but I still don't know why Chromium is behaving different in that aspect at your system than at mine, maybe I'll do a websearch about it later.

And I'm totally fine with your choice of Chromium, see my earlier posts, if you like:
[http://ubuntuforums.org/showpost.php?p=10553614&postcount=7](http://ubuntuforums.org/showpost.php?p=10553614&postcount=7)
[http://ubuntuforums.org/showpost.php?p=10554856&postcount=10](http://ubuntuforums.org/showpost.php?p=10554856&postcount=10)
[http://ubuntuforums.org/showthread.php?p=10547420](http://ubuntuforums.org/showthread.php?p=10547420)

---

