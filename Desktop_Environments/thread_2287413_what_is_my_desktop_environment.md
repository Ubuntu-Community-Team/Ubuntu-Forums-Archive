---
title: "what is my desktop environment?"
date: 2015-07-19
forum: Desktop Environments
---

### Post by jerry50 on 2015-07-19
I recently had Ubuntu 14.04 installed as a dual boot with Win. 7.  As I'm learning the terminology for linux, I'm having questions.  Like....which desktop environment do I have?

---

### Post by vasa1 on 2015-07-19
> **jerry50 said:**
> I recently had Ubuntu 14.04 installed as a dual boot with Win. 7.  As I'm learning the terminology for linux, I'm having questions.  Like....which desktop environment do I have?

Run```
env | grep XDG_CURRENT_DESKTOP
``` in your terminal.

---

### Post by jerry50 on 2015-07-19
Vasa1, thanks!!  This is fun...when it isn't frustrating.  Unity it is.

---

### Post by jerry50 on 2015-07-19
Now...how to I mark this as "Solved"?

---

### Post by Rex Bouwense on 2015-07-19
At the beginning of your thread, click thread tools and choose mark as solved.

---

### Post by deadflowr on 2015-07-19
It should be noted that in some releases of Ubuntu gnome-flashback may show up in the XDG_CURRENT_DESKTOP as unity.
fwiw
Reference thread here:
[http://ubuntuforums.org/showthread.php?t=2243854](http://ubuntuforums.org/showthread.php?t=2243854)

---

### Post by CantankRus on 2015-07-19
I have this handy command filed away that may help you understand things.
Requires wmctrl (90kb) to be installed.
Install via terminal....
```
sudo apt-get install wmctrl
```

Then in the terminal run....
```
echo -e "Session: $DESKTOP_SESSION\nDesktop: $XDG_CURRENT_DESKTOP \nWindow Manager: $(wmctrl -m | awk '/Name:/{print $2}')"
```
eg
```
[COLOR="#006400"]**glen@Trusty:~$[/COLOR] echo -e "Session: $DESKTOP_SESSION\nDesktop: $XDG_CURRENT_DESKTOP \nWindow Manager: $(wmctrl -m | awk '/Name:/{print $2}')"**
Session: ubuntu
Desktop: Unity 
Window Manager: Compiz
```

_**Tip**_: Keep notes in something like gnote as you learn.

---

