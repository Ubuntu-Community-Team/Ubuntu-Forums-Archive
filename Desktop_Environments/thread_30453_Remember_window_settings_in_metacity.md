---
title: "Remember window settings in metacity"
date: 2005-04-28
forum: Desktop Environments
---

### Post by joshmachine on 2005-04-28
Does anyone know of a way to make metacity remember settings for a particular apps windows.  

I'd like my gaim chat window to always "Appear on Visible Workspace" but I have to set it each time I launch the application and this really irks me.


Cheers

---

### Post by stevetone on 2005-04-29
I have had to use the utility "wmctrl" and run a startup script in ~/Desktop/Autostart (I use xfce -- I believe gnome uses a different autostart directory) to set window attributes (position, always-on-top, sticky) correctly.

I forget where I got wmctrl from -- I think I had to compile it myself. However, it will allow you to control application window attributes quite nicely -- google it!

---

### Post by doclivingston on 2005-04-29
Devil's Pie ([http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)) should be able to do what you want.

---

