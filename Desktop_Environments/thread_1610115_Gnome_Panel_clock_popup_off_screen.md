---
title: "Gnome Panel clock popup off screen"
date: 2010-10-31
forum: Desktop Environments
---

### Post by ChuckyDuckster on 2010-10-31
Hi all,

I recently upgraded from 10.04 to 10.10, and I love it! The only thing that is weird is this:

I installed mintmenu, and added launcher buttons for a few apps (looks like w7). Now on my gnome panel when I click the clock, the calendar and time zone popup shows at the very top of my screen, with most of it off screen. What could be causing this?

---

### Post by jajodo on 2010-11-14
Just installed linux mint 10 and same problem

---

### Post by jajodo on 2010-11-14
Found this old work around using compiz settings-->window management--> place windows--> fixed window placement-->windows with fixed positions.

-click new
-name=clock-applet
-for X position type 979
-for y position type 410
-click on "keep in work area"

These positions worked for me but you may have to experiment
Thanks to author of link below

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10088680](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10088680)

---

### Post by gaelanlloyd on 2010-11-18
I had the same issue.  It appears when Preferences --> Appearance --> Visual effects is set to Normal or Extra.

Thanks for the suggestion above, jajodo.  It worked for me, and I noticed that you don't have to worry too much about the screen dimensions as long as you have the "Keep in work area" selected.

My monitor resolution is 1366 x 768, and I want the clock-applet to be in the bottom right corner...  So, I entered the following and it worked perfectly:

Positioned windows = name=clock-applet
X Positions = 1366
Y Positions = 768
Keep in work area = Checked

---

### Post by tpapastylianou on 2011-01-03
> **jajodo said:**
> Found this old work around using compiz settings [...] 

Thanks jajodo, worked like a charm.
I see a bug has been filed in Gnome already as well.
I need to make a habit of checking out the forums early, not after I've already gotten frustrated with little bugs like this :)

---

