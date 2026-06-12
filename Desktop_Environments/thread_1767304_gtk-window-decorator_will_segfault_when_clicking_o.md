---
title: "gtk-window-decorator will segfault when clicking on windows menu icon"
date: 2011-05-25
forum: Desktop Environments
---

### Post by cokomonkey on 2011-05-25
I am running 11.04, and was running under Unity, and then moved back to Gnome 2.23.1

I am having a segfault occur any time I click on the window menu icon for any window. Once this occurs all the menu bars disappearing and I cannot move any of the windows, minimise/maximise, and while I am able to close most windows via their menu's it is really annoying!

To get it back up I have to call gtk-window-decorator from the command line. This is how I found out it was a segfault.

```
** (gtk-window-decorator:18789): CRITICAL **: Could not find frame info \xd0\u0012\x8f\u0008\u0001 in frame type table
Segmentation fault
```

Does anyone else notice anything like this?

Coko.

---

### Post by brainey on 2011-05-30
Yes - this just occurred for me - it at least the 2nd or third time I have had this crash metacity on me. 

From my .xsession-errors:
** (gtk-window-decorator:4611): CRITICAL **: Could not find frame info `.@      \u0001 in frame type table
Segmentation fault

Any one have clue on this ?

Thanks.

p.s.
I have to say I'm pretty disappointed by 11.04 - I don't think I've had as many crashes of application (metacity) and window environment (firefox / chrome crash which take the session with it and end up dumped back to the login window) as I've had in 11.04 than in any previous release over the last 5 years. I suspect the compiz stuff but need to do more data gathering. Some one suggested turning off flash in firefox which may or may not the solution - too early to say.

---

### Post by wildmanne39 on 2011-05-31
> **cokomonkey said:**
> I am running 11.04, and was running under Unity, and then moved back to Gnome 2.23.1

I am having a segfault occur any time I click on the window menu icon for any window. Once this occurs all the menu bars disappearing and I cannot move any of the windows, minimise/maximise, and while I am able to close most windows via their menu's it is really annoying!

To get it back up I have to call gtk-window-decorator from the command line. This is how I found out it was a segfault.

```
** (gtk-window-decorator:18789): CRITICAL **: Could not find frame info \xd0\u0012\x8f\u0008\u0001 in frame type table
Segmentation fault
```

Does anyone else notice anything like this?

Coko.Hi, I do not know what is causing the problem but you can use this command to restart gtk-window-decorator.
```
gtk-window-decorator --replace
```

---

### Post by doommaster on 2011-07-26
> **wildmanne39 said:**
> Hi, I do not know what is causing the problem but you can use this command to restart gtk-window-decorator.
```
gtk-window-decorator --replace
```

This is the default way to run gtk-window-deorator, but not solve the problem. I have exactly the same problem with my ubuntu 11.04

---

### Post by bwzz on 2011-07-28
I think this error is caused by a conflict between unity desktop and gnome desktop... I'm facing the same problem as well.

---

### Post by tsh on 2011-10-22
Opened a bug.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880018](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880018)

---

