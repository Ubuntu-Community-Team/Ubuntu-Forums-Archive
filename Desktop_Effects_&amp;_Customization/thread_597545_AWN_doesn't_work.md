---
title: "AWN doesn't work"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by Martje_001 on 2007-10-30
Hi,
I've compiled it from the source, but i get this message:
```
martijn@gutsy:~$ awn-manager
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:241: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 149, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 241, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue

```:confused:

Edit: Ubuntu 7.10

---

### Post by rosendahl on 2007-10-30
Same problem here.

---

### Post by chipwhisperer on 2007-11-02
Same problem here as well. I can't seem to find a solution on the web. Has anyone solved this problem? I know that Compiz needs to be activated, but does a certain plugin need to be on as well?

---

### Post by chipwhisperer on 2007-11-02
Actually, I may be an idiot, did you guys/gals try click on Applications -> Accessories -> Avant Window Navigator ? Cause then it seems to work.

---

### Post by Martje_001 on 2007-11-03
> **chipwhisperer said:**
> Actually, I may be an idiot, did you guys/gals try click on Applications -> Accessories -> Avant Window Navigator ? Cause then it seems to work.
Hmm.. It's works after installing the newer version. And yes it works via "Applications -> Accessories -> Avant Window Navigator" now ;)

---

### Post by Yoooder on 2007-11-04
Had me confused as well.  I had found the AWN manager under System / Settings and when it failed to load anything I tried both commands that are prefixed with "awn-" from the CLI and got errors.

In hindsight, I don't think the tutorials I followed ever said where the app would install to, or maybe I overlooked it.

---

### Post by sutem on 2007-11-13
I have same problem

---

### Post by dkarnows on 2007-11-20
I have the same problem, and Systems->Preferences->Awn manager doesn't work either. I'm running version 0.2.0-bzr142-01 of avant-window-navigator-bzr which I installed by following these instructions: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981) . That version is the currently the latest in that repository.

---

### Post by go_beep_yourself on 2007-11-21
Is there still not a solution to this problem?

---

### Post by jessedyer on 2008-05-02
I had the same problem; try running **avant-window-manager**

Once I did this once, the preferences manager started normally for me afterward.

---

### Post by mrbaze on 2008-06-07
> **jessedyer said:**
> I had the same problem; try running **avant-window-manager**

Once I did this once, the preferences manager started normally for me afterward.

Hi,
I had this exact problem and jessedyer's tip helped me, although it was 
avant-window-navigator

---

### Post by Victormd on 2008-06-07
have any of you tried AWN-BZR version?

---

