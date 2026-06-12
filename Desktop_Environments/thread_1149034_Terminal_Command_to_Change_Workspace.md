---
title: "Terminal Command to Change Workspace"
date: 2009-05-04
forum: Desktop Environments
---

### Post by secondstage on 2009-05-04
Every time that I turn on my computer, I open Rhythmbox, and Firefox. Is there a way to automate this process, but have Rhythmbox, and Firefox on its own workspace. So the command would something like this...
```
rhythmbox && [switch to workspace 2] && firefox
```

What would that middle part be, if I have Compiz Fusion, and cube desktop in place?

---

### Post by secondstage on 2009-05-07
2 Day Bump.

---

### Post by kanikilu on 2009-05-07
First you need to install the **wmctrl** package. If you weren't using compiz, that'd basically be it...

It's more complicated with compiz, but fortunately someone has been kind enough to write a script:

[http://sfyang-en.blogspot.com/2008/02/rotate-cube-in-compiz-with-wmctrl.html](http://sfyang-en.blogspot.com/2008/02/rotate-cube-in-compiz-with-wmctrl.html)

---

### Post by hictio on 2009-05-07
You should take a look at [wmctrl](http://tripie.sweb.cz/utils/wmctrl/).

> 
The wmctrl program is a UNIX/Linux command line tool to interact with an EWMH/NetWM compatible X Window Manager.


---

### Post by mr_skater99 on 2009-10-19
The script linked to is fantastic - however it only works if run in a terminal on the desktop.

What i would like to do is cron this script.  We have a monitoring box on the wall that displays about 4 workspaces of stats and i want it to automatically flip through them at regular intervals.

When i cron this though i get the error "Cannon open display"

Anyone have any idea about how to cron this script so it can run in the background - and not in a terminal on the desktop?

---

### Post by virpara on 2012-06-10
How to use wmctrl?
 wmctrl -s 1 Doesn't work?

---

### Post by sffvba[e0rt on 2012-06-10
*Old thread **closed**.*


404

---

