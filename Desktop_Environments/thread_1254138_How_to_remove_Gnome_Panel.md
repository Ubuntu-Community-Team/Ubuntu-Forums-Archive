---
title: "How to remove Gnome Panel"
date: 2009-08-31
forum: Desktop Environments
---

### Post by ductiletoaster on 2009-08-31
Ok so i installed tint2 and now i would like to remove the final gnome panel. So lets hear the suggestions! Thanks ahead

---

### Post by steveneddy on 2009-08-31
Right click the panel and select Delete This Panel

---

### Post by ductiletoaster on 2009-08-31
lol yeah thats how you remove panels.... except the last one. When ur down to one it doesnt work. its greyed out


Ok so is there a way to shutdown gnome-panels....

1) delete
or
2) config file trick
or
3) uninstall

---

### Post by colau on 2009-08-31
> **ductiletoaster said:**
> lol yeah thats how you remove panels.... except the last one. When ur down to one it doesnt work. its greyed out


Ok so is there a way to shutdown gnome-panels....

1) delete
or
2) config file trick
or
3) uninstall
What do you mean by ***shutdown gnome-panels....***

---

### Post by jocko on 2009-08-31
> **colau said:**
> What do you mean by ***shutdown gnome-panels....***
I'm pretty sure he means exactly what he says. He wants to remove the last gnome-panel...

Unfortunately I have no idea how to do that...

---

### Post by ATL™ on 2009-08-31
have you tried pkill gnome-panel?

---

### Post by Nepherte on 2009-08-31
> **ATL&#8482 said:**
> have you tried pkill gnome-panel?
I believe gnome-panel will respawn in that case. Removing the gnome-panel might do the trick if no other important packages depend on it (guess not). Another possibility is to just move the /usr/bin/gnome-panel to /usr/bin/gnome-panel.backup, a little ugly but then again, it might do the trick.

---

### Post by benerivo on 2009-08-31
The easiest way i have removed the last panel, is to add gnome-panel as a start up item in System>Preferences>Sessions, and then untick it so it doesn't start up on log in. I think this has been suggested above. The command for the new item should just read...```
gnome-panel
```EDIT - be warned that doing this will remove not only the panel, but also the Alt+F2 launcher.

---

### Post by asmoore82 on 2009-08-31
```
gconf-editor
```
and poking around in "/desktop/gnome/session" may be in order.

I only know of these keys because Ubuntu's netbook launcher chooser has a tendency to break them.

---

### Post by dumblebee100 on 2009-08-31
> **ductiletoaster said:**
> Ok so i installed tint2 and now i would like to remove the final gnome panel. So lets hear the suggestions! Thanks ahead

I get your problem ...I also faced the same problem when I installed Avant window navigator ..the gnome panel doesnt delete the last one ...I did everything possible ....

I even removed the executable of gnome-panel from the /usr/bin directory ..but somehow after reboot it appears again ...I dont get how it got gnome-panel executable when I removed it from its original location ...I think it has some backup or so ...

so after a wide search for this topic there was a little solution ...we cant disable the last panel ..but we can hide it ..so that it doesnt bother anymore ...
Im posting you by backup file where I wrote something about disabling and enabling the gnome-panel ..

```
these are default values for gnome panel

location gconf-editor /apps/panel/toplevesl/

auto hide =false
auto_hide_size=6
expand=yes
hide_delay=500
monitor=6
unhide_delay=500
x=0
y=0


to disable it 

Open gconf and goto /apps/panel/toplevels and set these values:
auto_hide: yes
auto_hide_size: 1
expand: no
hide_delay: 1
monitor: 3
unhide_delay: 10000
x: 10000
y: 10000

This will hide the panel permanently

```

---

### Post by ductiletoaster on 2009-08-31
Sorry it took me so long to reply... thanks to everyone for there responses. The reason i didnt reply is because well i totally messed up. Basically tried somthing and lost all fuctionality and so i opt to reinstall. but now i am back! I have tried almost all those suggestions. Sep dumblebee100's... have you tried this cus this is similiar to what i did. will i still have ALT F2 and all. The panel still exsists its just hidden?

---

### Post by steveneddy on 2009-09-01
If you don't like panels then have them autohide or maybe try using Fluxbox.

---

