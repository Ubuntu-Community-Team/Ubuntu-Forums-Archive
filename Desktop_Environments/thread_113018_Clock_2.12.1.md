---
title: "Clock 2.12.1"
date: 2006-01-05
forum: Desktop Environments
---

### Post by madebyjerry on 2006-01-05
I have been searching around to find how to change format from:

weekday, date month, time

to:

weekday, month date, time

I've tried dpkg-reconfigure locales to no avail.

I'm just learning to use Ubuntu, so assistance would be appreciated.

Jerry

---

### Post by nalmeth on 2006-01-05
I'm sorry if you have tried this and my answer is redundant, but can't you just right click the clock, and configure these types of things in its preferences? KDE you certainly can, and I'm relatively sure with gnome aswell.

---

### Post by ysse on 2006-01-05
The time format should follow your locale. What language settings did you choose when installing? If I select English (US) for the session, i get the time format you want, but if I use my default Swedish i get weekday, date, month, hour.minute. 

If you right-click, you do get to set some preferences like 12/24 hour time, but in keeping with the Gnome philosophy, you don't see everything there is to set up front, as opposed to KDE. (This is the subject of many a flame war, but let's not delve into that now...) 

To be sure, you **can** set a custom date format, but you need to know about format strings according to the C library function strftime(). And to set it you need to use the Configuration Editor. From the menus: Applications - System Tools - Configuration Editor.

To just do what you asked for: In the Configuration Editor, navigate to /apps/panel/applets/clock_screen0/prefs. Set the key "custom_format" to ```
%a %b %e, %H.%M
```, and "format" to ```
custom
```.

---

### Post by madebyjerry on 2006-01-06
Thank you so much. This is what I needed.

Jerry

---

### Post by groggyboy on 2006-06-16
Bringing up an old thread.
> %a %b %e, %H.%M
It works like a charm.  I modified it to say:
> %b %e, %H:%M %p
But it still displays the time as 24hr.  How do I change it to 12hr format?
groggyboy

---

### Post by dcstar on 2006-06-17
[QUOTE=groggyboy]Bringing up an old thread.

It works like a charm.  I modified it to say:

But it still displays the time as 24hr.  How do I change it to 12hr format?
groggyboy[/QUOTE]
Try "I:" instead of "H":

[http://au2.php.net/strftime](http://au2.php.net/strftime)

---

### Post by groggyboy on 2006-06-18
Thanks.  It's exactly what I wanted.  And the link is pretty handy too!

---

### Post by euchrid on 2006-12-13
I found [this]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=d/date") pretty helpful for further configuration. Next step: make my own calendar...

---

