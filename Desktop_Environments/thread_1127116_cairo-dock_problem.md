---
title: "cairo-dock problem"
date: 2009-04-16
forum: Desktop Environments
---

### Post by bded on 2009-04-16
i think i messed up, cairo-dock was working until i switched it to the ubuntu theme now it won't load when i alt-f2 it.

ubuntu 8.10 intrepid.

please excuse the noobishness.

got this by running in terminal.

---

### Post by MaindotC on 2009-04-16
What repository did you use to install this?

---

### Post by bded on 2009-04-16
[http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

i added this to the list, then further googling showed that i could get it thru the synaptic packagemanager so i did it that way.

on hindsight i probably should have removed that line from the list before updating.

how do i undo the mess i have made?

[edit]

i am removing that line and uninstalling all cairo-dock by sudo apt-get autoremove cairo-dock cairo-dock-plug-ins

i will then try to install thru synaptic

[edit2]

it works now lol. sorry for posting, i've only had a few days with ubuntu.

---

### Post by MaindotC on 2009-04-16
Np - in the future you can view a list of packages that were installed/updated in Syanptic so you can uninstall them in the event there's a problem and revert back to your original state.

---

### Post by bded on 2009-04-16
rather than make  a new thread i have an issue with the applets. i don't have any and i am unsure how to get any. pic related

also: i noticed in synaptic that my cairo-sock-plug-ins is version 1.6.3.1 but my cairo-dock is version 1.6.2.3-0ubuntu1 with 1.6.3.1 as an available update but the update fails with this error:

E: /var/cache/apt/archives/cairo-dock_1.6.3.1_all.deb: trying to overwrite `/usr/share/cairo-dock/icon-mouse.png', which is also in package cairo-dock-data

---

### Post by bded on 2009-04-16
bumps allowed? :popcorn:

---

