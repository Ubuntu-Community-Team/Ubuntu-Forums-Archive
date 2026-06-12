---
title: "Found a bug on the panel - solved"
date: 2013-07-14
forum: Desktop Environments
---

### Post by PaulBx on 2013-07-14
First post, hello all.

I noticed some reviews of lubuntu mentioned a goofed up clock in the task bar. When I installed and updated, mine was like that too. I went to "Panel Settings" aka "panel preferences" and selected the "panel applets" tab. There I found two instances of "application launch bar", one in the normal position and one at the end of the list. I deleted the latter and my clock now looks good.

Maybe this has been discovered already but I thought I'd mention it just in case.

I have installed on a Lenovo G780 and so far it looks good. Full disk encryption and using an SSD drive, OCZ Vertex4. I thought it strange the installer insisted I needed LVM in order to get full disk encryption.

---

### Post by Rex Bouwense on 2013-07-14
Not sure if that is a bug.  The first Application Launch Bar deals with your quick launch icons on the task bar.  The second (at least on mine installed version of Lubuntu 13.04) has only the shutdown icon.  I have never messed with it.  It is a little confusing why that would be there but I have never questioned it before.

---

### Post by PaulBx on 2013-07-14
Ah, I guess I mistook what was going on there, and the review complaints about it. Anyway I got rid of that icon which bothered me...

---

### Post by Dennis N on 2013-07-14
Rex is correct. No bug.

In Lubuntu, any Application Launcher on a panel must be placed within an Application Launch Bar. To have the Shutdown application where it is, you must have a Application Launch Bar on the extreme right to "hold" it's launcher. You can create multiple panels (I add one on the left that autohides a launch bar). 

Other stuff on the panel are applets (clock) and indicators (battery).

In Xubuntu by contrast, application launchers go **directly** onto a panel.

---

