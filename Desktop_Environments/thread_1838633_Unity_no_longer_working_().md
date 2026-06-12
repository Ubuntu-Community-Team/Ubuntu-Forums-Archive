---
title: "Unity no longer working (?)"
date: 2011-09-04
forum: Desktop Environments
---

### Post by DanH42 on 2011-09-04
I've had Ubuntu 11.04 installed on my laptop for a week or so now. Just today, it started freezing as soon as I tried opening any applications (Chrome, Terminal, gedit, etc). I restarted in Failsafe graphics mode with Unity disabled, and everything's working fine. What should i try to get Unity working again (since I'm assuming that's where the problem is)?

---

### Post by raja.genupula on 2011-09-04
enable unity from by editing settings at compfiz settings 

type ```
ccsm
``` in terminal 
if it is not installed then install it . its gonna give you the installation way if it is not installed . all the best .

---

### Post by DanH42 on 2011-09-04
> **raja.genupula said:**
> enable unity from by editing settings at compiz settings

Enabling Unity through Compiz doesn't seem to actually... enable Unity. Not that I can tell, anyway. Also, Unity has no problem enabling itself when I boot my OS normally. The launcher comes up and everything. I only experience trouble when I try launching a program.

---

### Post by howefield on 2011-09-04
Have you tried resetting Unity to default settings, in terminal type..

```
unity --reset
```

---

### Post by DanH42 on 2011-09-04
> **howefield said:**
> Have you tried resetting Unity to default settings, in terminal type..

```
unity --reset
```

```

$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Segmentation fault

```

Also, now that I've run that, none of my windows have title bars, and I can't minimize them (they all seem to be in "Always On Top" mode).

EDIT:
When I rebooted, the Ubuntu splash screen came up for a split second, then the screen went black and nothing else happened. This continued for a dozen or so reboots, then Unity finally came up normally. It still freezes as soon as it tries opening a window.

---

