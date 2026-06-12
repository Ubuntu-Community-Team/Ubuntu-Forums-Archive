---
title: "nm-applet error"
date: 2008-01-24
forum: Desktop Environments
---

### Post by lsutiger on 2008-01-24
I was trying to change the screensaver settings. When I selected screensaver, X restarted on its own. When I logged back in I received this error:
```
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
``` with the heading:
```
An error occurred while loading or saving configuration information for nm-applet. Some of your configuration settings may not work properly.

```

Now when ever I try to open the screensaver app, X restarts.

I tried deleting ~/.gconf/saved_state [per this post]("http://ubuntuforums.org/showthread.php?t=93314").

I am pretty lost on what to do. Any help would be appreciated.

---

### Post by lsutiger on 2008-01-24
UPDATE: Reinstalled gnome-screensaver, did no good.

---

### Post by lsutiger on 2008-01-26
bump

---

### Post by lsutiger on 2008-01-31
bump!

---

### Post by lsutiger on 2008-02-04
Anybody?

I tried a complete remove and a clean instal of screensaver. That worked for one day...back at square one.

---

### Post by lsutiger on 2008-02-09
bump

---

### Post by tcommbee on 2008-02-09
did you try running gnome-screensaver-preferences from terminal?

---

### Post by lsutiger on 2008-02-09
OK..I un-installed and reinstalled again. ran from the terminal..Works fine. Will report back if this happens again.

---

### Post by lsutiger on 2008-02-09
Well, it worked for a while, but the screensaver never comes on. And when opening the screensaver preference dialog, it reset X...

should I delete the config file??

---

### Post by lsutiger on 2008-02-20
Bump...still having problem....even running gnome-screensaver-preferences in terminal crashes X

---

