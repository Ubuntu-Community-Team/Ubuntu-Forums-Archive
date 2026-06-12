---
title: "Screenlets manager won't open"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by enchance on 2007-10-26
I'm using the latest version of screenlets but suddenly the screenlets-manager won't open. It would open for less than a sec then close all of a sudden. My screenlets are still intact but how can I add more if the manager won't open?

---

### Post by momentsb4autumn on 2007-10-27
I am experiencing the same exact thing. When I first installed it was running fine and I could use the screenlet apps with no problem. After a short while I tried to open the manager again and it would look like it was going to open and then 1 sec. later it just closed and disappeared. I tried doing this many times and I come up with the same result. Does anyone have an idea on how to fix this problem? Thanks!





momentsb4autumn

---

### Post by skompier on 2007-10-27
Open a Terminal and do the following:

```
cd /usr/local/share/
```

type:

```
screenlets-manager
```

See if there are any error messages.

---

### Post by momentsb4autumn on 2007-10-27
Unable to load 'Slideshow' from /usr/local/share/screenlets/Slideshow: No module named Image 
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in <module>
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 133, in __init__
    self.load_screenlets()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 259, in load_screenlets
    info = ScreenletInfo(s, meta['name'], meta['info'], meta['author'], 
TypeError: 'NoneType' object is unsubscriptable




These are the error messages when I did what you said
:guitar:


^_^

---

### Post by skompier on 2007-10-27
It looks like you have SlideShow enabled but you don't have python-imaging installed.

Go to System>Administration>Synaptic Package Manager> and search for python-imaging and install that.

---

### Post by momentsb4autumn on 2007-10-27
thanks man....


that did the trick, I appreciate the help!




God Bless,
momentsb4autumn

---

### Post by skompier on 2007-10-27
> **momentsb4autumn said:**
> thanks man....


that did the trick, I appreciate the help!




God Bless,
momentsb4autumn

Glad that I was able to help. Enjoy...:)

---

### Post by tombott on 2007-11-06
> **skompier said:**
> It looks like you have SlideShow enabled but you don't have python-imaging installed.

Go to System>Administration>Synaptic Package Manager> and search for python-imaging and install that.

Superb, yet again a simple google search sorted my problem.
Thanks skopmier and thanks ubutnu forums!

---

### Post by enchance on 2007-11-07
I tried installing python-imaging like you said but the prob still occurs. The panel shows for alike half a sec then disappears. I get this after running screenlets-manager
```

LISTED PATH NOT EXISTS: /usr/local/share/screenlets/crystal_blue
Unable to load 'WorldClock' from /usr/local/share/screenlets/WorldClock: No module named dateutil.tz 
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in <module>
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 133, in __init__
    self.load_screenlets()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 259, in load_screenlets
    info = ScreenletInfo(s, meta['name'], meta['info'], meta['author'], 
TypeError: 'NoneType' object is unsubscriptable


```

Is my prob serious?

---

### Post by JTJones on 2007-11-07
> **tombott said:**
> Superb, yet again a simple google search sorted my problem.
Thanks skopmier and thanks ubutnu forums!

nice tip, thanks :D

---

### Post by itsjustarumour on 2007-11-08
> **enchance said:**
> I'm using the latest version of screenlets but suddenly the screenlets-manager won't open. It would open for less than a sec then close all of a sudden. My screenlets are still intact but how can I add more if the manager won't open?

I had exactly the same problem on a fresh Gutsy install.  Uninstalled Screenlets, then re-installed, and Hey Presto - been working fine ever since!

---

### Post by enchance on 2007-11-08
I got it! the WorldClock screenlet was the one causing the screenlet manager to close. I just had to delete it in root and that was it! [SIZE="3"][SIZE="4"]Guys, don't download the WorldClock screenlet. It will cause your screenlet manager to close abruptly.[/SIZE][/SIZE]

---

### Post by binnaeus on 2008-03-05
> **enchance said:**
> I got it! the WorldClock screenlet was the one causing the screenlet manager to close. I just had to delete it in root and that was it! [SIZE="3"][SIZE="4"]Guys, don't download the WorldClock screenlet. It will cause your screenlet manager to close abruptly.[/SIZE][/SIZE]

Had the same problem, screenlets would work fine until WorldClock is installed. I fixed this by installing python-dateutil which you can look up from Synaptic.

---

