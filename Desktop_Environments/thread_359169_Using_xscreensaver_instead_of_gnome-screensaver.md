---
title: "Using xscreensaver instead of gnome-screensaver"
date: 2007-02-11
forum: Desktop Environments
---

### Post by Dylnuge on 2007-02-11
Hello,

I prefer the Xscreensaver configuration tool to the gnome-screensaver tool. I have installed it with synaptic, how do I make Ubuntu use it instead of gnome-screensaver?

Thanks,
Dylan

---

### Post by Rui Pais on 2007-02-11
sudo apt-get remove gnome-screensaver
sudo aptitude install xscreensaver

:)

---

### Post by Dylnuge on 2007-02-12
I installed xscreensaver, and removed gnome-screensaver.

Now there is no screensaver option in prefrences. If I add a link to xscreensaver-prefrences, will it just use xscreensaver?

---

### Post by Rui Pais on 2007-02-12
run xscreensaver-demo from a terminal and set your preferences, like time till start, etc.

it should be the only thing needed...

you could add a link to xscreensver-demo somewhere on menus, prefrences, whatever you prefer, to easily access the preference windows. Makes life easy, yes. :)

---

### Post by ayoli on 2007-02-12
if you want Xscreensaver auto starts at each session, add this:
```
xscreensaver -no-splash
```
via menu System > Preferences > Session and tab "startup programms".
Use alacarte menu editor to add an entry in menu.

---

### Post by Dylnuge on 2007-02-12
Isn't that supposed to be
```
 --no-splash 
```

Thanks for the help.

---

### Post by sanicki on 2007-03-01
New user here. Will xscreensaver let me run screensavers behind the login as described here:
[http://gentoo-wiki.com/TIP_Screensaver_in_Background](http://gentoo-wiki.com/TIP_Screensaver_in_Background)

?

Thanks in advance.

---

### Post by 23meg on 2007-03-01
[QUOTE=Dylnuge]
I prefer the Xscreensaver configuration tool to the gnome-screensaver tool. I have installed it with synaptic, how do I make Ubuntu use it instead of gnome-screensaver?[/QUOTE]

I wrote a guide on doing just that:

[http://www.ubuntuforums.org/showthread.php?t=195557](http://www.ubuntuforums.org/showthread.php?t=195557)

Also another, which lets you tweak the settings without replacing gnome-screensaver altogether:

[http://www.ubuntuforums.org/showthread.php?t=198809](http://www.ubuntuforums.org/showthread.php?t=198809)

---

### Post by sanicki on 2007-03-01
Tried your guide (second one), but the screen capture savers still don't work under Gnome (though they look great when previewed in xscreensaver). Am I doing something incorrectly? Also still get nothing underneath my login.

---

### Post by 23meg on 2007-03-01
> **sanicki]Tried your guide (second one), but the screen capture savers still don't work under Gnome [/QUOTE]I recall they used to work when I tested the guide said:**
> Also still get nothing underneath my login.I didn't post in response to your question, but to that of the original poster; I have no idea if the login trick will work.

---

