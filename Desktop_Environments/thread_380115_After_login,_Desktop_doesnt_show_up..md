---
title: "After login, Desktop doesnt show up."
date: 2007-03-09
forum: Desktop Environments
---

### Post by Kastang on 2007-03-09
Ubuntu boots up fine up fine, when I get to the login screen i enter my U&P when I press enter though to login, a tan screen comes up and just hangs there, I have let it sit now for 10 minutes and It has not done anything, I tried restarting and choosing Failsafe Gnome but it does the same thing.

---

### Post by Kastang on 2007-03-09
Any suggestions? I have been over 2 months now without any real issues that forced me to reformat.

---

### Post by moore.bryan on 2007-03-09
*it sounds as though x isn't starting.  what happens when you right-click?*

---

### Post by Kastang on 2007-03-09
> **moore.bryan said:**
> *it sounds as though x isn't starting.  what happens when you right-click?*


Nothing happens at all when I right click.

---

### Post by moore.bryan on 2007-03-09
*then i'm sure its x not starting.  try choosing recovery and when it comes to the prompt, type ```
startx
```what happens?*

---

### Post by Kastang on 2007-03-09
> **moore.bryan said:**
> *then i'm sure its x not starting.  try choosing recovery and when it comes to the prompt, type ```
startx
```what happens?*


what I startx from recovery mode.. it works fine :confused: Desktop booted up.

---

### Post by moore.bryan on 2007-03-10
[I]that's not bad; that's good... gives us information.  edit your ~/.xinitrc file to read 
```
#!/bin/sh
startx
```
and that SHOULD fix the problem...

repost info, too!  ;-)
[/I]

---

### Post by Kastang on 2007-03-10
It worked! Thankyou very much for the help moore.bryan!

---

### Post by mwagz on 2007-03-11
I have a similar problem and I tried this methos....it works but with one difference. 
I logged into recovery mode and entered startx.
I added startx in the xinitrc file.
I logged off in normal mode but the desktop didnt come up.I was presented with the login console commandline.
When I enter startx i'm presented with the gnome desktop but how do i get my original desktop?

---

### Post by moore.bryan on 2007-03-12
[I]"original desktop?"  what do you mean?  had you made changes to it?  please give some additional details; thanks!

if you want to "jump the gun" a bit, you could delete the .xinitrc file and type 
```
cp /etc/X11/xinit/xinitrc ~/.xinitrc
```[/I]

---

