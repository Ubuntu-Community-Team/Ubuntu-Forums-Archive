---
title: "Gnome Panel Applet Refresh"
date: 2010-02-10
forum: Desktop Environments
---

### Post by ClintSwiney on 2010-02-10
I was in need of a new Gnome panel applet and found what I was looking for no problem. For grins it's link-monitor-applet. So I found it in Synaptic Package Manager and installed it from there. But it did not show up in the Add to Panel options. So I uninstalled it and installed it from the command line using apt-get, still nothing in the Add to Panel Dialogue. I removed it and installed it using Aptitude and got the same thing, no option in Add to Panel list. I tried adding a custom applet and naming it link-monitor-applet, which gave an error when clicking on it. So I thought, There must be a way to refresh the Gnome Panel applets list, but did not find a way to do so. I ended up logging out and back in and wala Link Monitor shows up and can be easily added.

My question is this, is there a command or something that needs to be done to refresh the Gnome Panel applet list to display a newly installed applet, short of Logging off then back on?

---

### Post by TheNessus on 2010-02-10
> **ClintSwiney said:**
> I was in need of a new Gnome panel applet and found what I was looking for no problem. For grins it's link-monitor-applet. So I found it in Synaptic Package Manager and installed it from there. But it did not show up in the Add to Panel options. So I uninstalled it and installed it from the command line using apt-get, still nothing in the Add to Panel Dialogue. I removed it and installed it using Aptitude and got the same thing, no option in Add to Panel list. I tried adding a custom applet and naming it link-monitor-applet, which gave an error when clicking on it. So I thought, There must be a way to refresh the Gnome Panel applets list, but did not find a way to do so. I ended up logging out and back in and wala Link Monitor shows up and can be easily added.

My question is this, is there a command or something that needs to be done to refresh the Gnome Panel applet list to display a newly installed applet, short of Logging off then back on?

just kill the gnome-panel process, and it would immediately revive itself. same effect as logging out.

---

