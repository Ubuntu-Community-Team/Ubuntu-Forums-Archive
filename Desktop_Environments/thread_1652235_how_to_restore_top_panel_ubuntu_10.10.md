---
title: "how to restore top panel ubuntu 10.10"
date: 2010-12-24
forum: Desktop Environments
---

### Post by sevenenemy on 2010-12-24
i hid the top panel from the right click menu the top panel gave me by default and now i cannot find how to restore it to default and get the top panel back. please help, thanks.

---

### Post by karthick87 on 2010-12-24
To reset the gnome panel to defaults, type this in a terminal
```
 gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

### Post by rapidrocket7 on 2010-12-24
Either you right click an existing panel and add a panel from there, or right click the desktop and add a panel from there. I can't remember exactly as I haven't used GNOME in a while.

---

### Post by ImDougy on 2010-12-24
did u delete the panel? if u did right click the bottom panel and click add panel, then add all the stuff back to that panel which would be... menu bar, notification area, indicator applet, clock, and indicator applet session... all organized in that order :D

---

### Post by Syed75 on 2010-12-24
Just right click add panel. Then add all the stuff in order to the menu. Applications Places etc..

---

### Post by sevenenemy on 2010-12-25
[karthick87]("http://ubuntuforums.org/member.php?u=891422")'s reply is the easiest and most straight-forward. thanks a lot and merry christmas.

---

### Post by tegiacden on 2011-01-01
> **karthick87 said:**
> To reset the gnome panel to defaults, type this in a terminal
```
 gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

Thanks alot, you saved my dat :D

---

### Post by karthick87 on 2011-01-02
You are welcome :)

---

### Post by samisam on 2011-01-02
Hi All,
I think I have either the same or similar problem-refer to the pic below.
The issue became an issue when I checked an auto hide option. Then I receive that screen.
Any ideas how to resolve it? it is a virtual Ubuntu 10.10 installed on Win XP. 
regards
Sam

---

### Post by karthick87 on 2011-01-02
@samisam this thread is marked as solved and so not many users will look at this thread..It's better to open a new thread..

---

### Post by samisam on 2011-01-02
Fortunately, I have managed to solve the problem, so that issue i really SOLVED.
Best regards and Happy New Year!

---

### Post by karthick87 on 2011-01-02
Thankyou and wish you the same :)

---

### Post by wsuchacz on 2011-01-07
Thank you karthick87, I fixed my problem with your info:D

---

### Post by ragavendra_bn on 2011-01-18
thks Karthick............

---

### Post by balaji31d on 2011-01-23
> **karthick87 said:**
> To reset the gnome panel to defaults, type this in a terminal
```
 gconftool --recursive-unset /apps/panel && killall gnome-panel 
```


Thanks. This worked great :)

---

### Post by josephmills on 2011-07-05
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```


THANKS 

Worked great

---

