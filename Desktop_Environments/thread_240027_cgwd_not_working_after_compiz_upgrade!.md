---
title: "cgwd not working after compiz upgrade!"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Jabran Asghar on 2006-08-20
Hi,

Just upgraded Comiz packages on Dapper, and cgwd stopped working.

No windows borders after executing "cgwd --replace -&", and following error is displayed:

> 
** (cgwd:11524): WARNING **: Cannot open pixmap: help

** (cgwd:11524): WARNING **: Cannot open pixmap: menu

** (cgwd:11524): WARNING **: Cannot open pixmap: shade

** (cgwd:11524): WARNING **: Cannot open pixmap: above

** (cgwd:11524): WARNING **: Cannot open pixmap: unabove

** (cgwd:11524): WARNING **: Cannot open pixmap: sticky

** (cgwd:11524): WARNING **: Cannot open pixmap: unsticky

** (cgwd:11524): WARNING **: Cannot open pixmap: unshade
Segmentation fault


I cannot use cgwd themes now :-(

My compiz start script is 

> 
#!/bin/bash

gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

cgwd --replace &

xmodmap /usr/share/xmodmap/xmodmap.ch


I also tried using starting cgwd before genome-windows decorator as well as doing a full dist-upgrade, but no luck.

Any hint how to correct the problem??

Jabran

---

### Post by desperado666 on 2006-08-20
killall gnome-window-decorator
wait

cgwd &
compiz --replace gconf &
xmodmap /usr/share/xmodmap/xmodmap.ch

---

### Post by Jabran Asghar on 2006-08-20
Just tried this .... but the same result, segmentation fault at the end, and no window borders.

Any other hint?

---

### Post by dentaku65 on 2006-08-20
The last dist-upgrade install the new cgwd (0.59) that fix the problem ;)

---

### Post by Jabran Asghar on 2006-08-20
I checked that I have cgwd 0.58. Doing a dist-upgrade or upgrade tells that everything is latest. How did you get the verison 0.59?

---

### Post by deeek on 2006-08-20
> **Jabran Asghar said:**
> I checked that I have cgwd 0.58. Doing a dist-upgrade or upgrade tells that everything is latest. How did you get the verison 0.59?
Did you do a

```

apt-get update

```

first?

---

### Post by Jabran Asghar on 2006-08-20
Ok, I just did "apt-get update" and then dist-upgrade, it downloaded the cgwd 0.59. cgwd works now :-)

Thanks.

---

### Post by jimmygoon on 2006-08-20
If anyone is feeling adventerous give this a shot
"nohup cgwd --replace &" and see if that makes it more responsive... it has for me a ton!

---

### Post by jake01 on 2006-08-20
Hello!

Interesting -- I'm getting the exact same set of errors. I'm totally up-to-date with cgwd and compiz, but those pixmap errors keep coming up.

Could it have to do with the theme I'm using? My intent is just to use the default theme (I think that's human-zootreeves, but it looks out of date)... if that's not right can someone point me in the right direction? I think I'm set up in a pretty standard way:

```
#!/bin/sh 
killall cgwd 
wait

cgwd & 
compiz --replace gconf &

```

I'm pretty sure the errors are themeing-related:

```
** (cgwd:5651): WARNING **: Cannot open pixmap: help

** (cgwd:5651): WARNING **: Cannot open pixmap: menu

** (cgwd:5651): WARNING **: Cannot open pixmap: shade

** (cgwd:5651): WARNING **: Cannot open pixmap: unshade

** (cgwd:5651): WARNING **: Cannot open pixmap: above

** (cgwd:5651): WARNING **: Cannot open pixmap: unabove

** (cgwd:5651): WARNING **: Cannot open pixmap: sticky

** (cgwd:5651): WARNING **: Cannot open pixmap: unsticky
```

---

### Post by rgsproductions on 2006-08-20
According to compiz.net, the repos on the ubuntu side were or are out of sync?  I up-dated to the .59 and the controls came back, but the buttons dont line up.  It still states in the themer that there is no cwgd, but the themes do switch now.  Hopefully there will be a magic fix.  Also somebody related that there is a problem with the opac plug in.:confused:

---

### Post by jake01 on 2006-08-20
That's weird... I've got version .59 and don't have any window borders etc.

- Jake

---

### Post by neymac on 2006-08-21
+1

I downgrade to cgwd_057 and solve the problesm.

```
cd /var/cache/apt/archives
sudo dpkg -i cgwd_0.57_i386.deb
```

---

### Post by neymac on 2006-08-21
+1

I downgrade to cgwd_057 and solve the problesm.

```
cd /var/cache/apt/archives
sudo dpkg -i cgwd_0.57_i386.deb
```

---

### Post by andrewguy9 on 2006-08-29
I'm having the same trouble, but with version .65

I have no window decorations and get 
"Cannot open pixmap: unsticky" messages.

Anyone know how to get my title bar back?

---

### Post by colonelk on 2006-08-30
me too with .66

exact same stuff as andrewguy9

help!

---

