---
title: "Remove Firefox &quot;Title Bar&quot;"
date: 2009-02-08
forum: General Help
---

### Post by Flynn555 on 2009-02-08
Hello i have a netbook and im trying to maximize screen real estate.  Is there any what to remove the firefox "Title bar" not the menu bar, the title bar ... the one with the minimize maximize close buttons on it.  i realize i could just go full screen but i still want to see the gnome panels. 


thanks.

---

### Post by geirha on 2009-02-08
In addition to maximizing and minimizing, there's also fullscreen mode. Hit F11 to toggle.

EDIT: Oops sorry, should have read the whole post before I replied. You already know about fullscreen mode. Don't think there's any way to remove the titlebar in metacity or compiz. Som other window managers has that ability though. fluxbox is one.

---

### Post by Nepherte on 2009-02-08
Yes, there is. One solution that comes to my mind is to use devilspie: [https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie) and use the undecorate option. You could use the following firefox.ds file:
```
(if (contains (application_name) "Mozilla Firefox") 
        (begin
                (undecorate)
        )
)
```

---

### Post by drs305 on 2009-02-08
This is certainly different - usually people want to *regain* their title/min/max bar...

Using reverse engineering, 
if:
1) you use compiz
and
2) you have "Windows Decoration" enabled
then:
Disabling/unticking the "Windows Decoration" checkbox may hide the titlebar. Unfortunately, it will do so on all apps. I doubt that you will really like that result since it effects all the screens, but it may do what you want.

Added: Nepherte has the right approach I think although Devilspie can have a steep learning curve. But if his solution doesn't solve it working with window decorations in compiz might.

---

### Post by Flynn555 on 2009-02-08
> **drs305 said:**
> This is certainly different - usually people want to *regain* their title/min/max bar...

Using reverse engineering, 
if:
1) you use compiz
and
2) you have "Windows Decoration" enabled
then:
Disabling/unticking the "Windows Decoration" checkbox may hide the titlebar. Unfortunately, it will do so on all apps. I doubt that you will really like that result since it effects all the screens, but it may do what you want.

Added: Nepherte has the right approach I think although Devilspie can have a steep learning curve. But if his solution doesn't solve it working with window decorations in compiz might.


Yay! I got it

Went to CCSM > Window Decorations and under Decoration windows i added !title=Web Browser 

(if you are wondering why web browser and not firefox its becuase the mini 9 has this stupid unbranded version of firefox.)

thanks guys...

---

