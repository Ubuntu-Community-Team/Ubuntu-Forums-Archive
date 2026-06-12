---
title: "Screen Resolution Help"
date: 2008-10-16
forum: Desktop Environments
---

### Post by dveisenhower on 2008-10-16
I searched around for a bit, and none of it made sense to me or seemed to have to do with my problem. I change the screen resolution from default to 1280x1024 and my screen either takes up half of the monitor or it freaks out and starts sliding across horizantally really quickly and I can control it with my mouse. :(

I really like this Ubuntu so far, but this might hold me back from converting.

---

### Post by overdrank on 2008-10-17
> **dveisenhower said:**
> I searched around for a bit, and none of it made sense to me or seemed to have to do with my problem. I change the screen resolution from default to 1280x1024 and my screen either takes up half of the monitor or it freaks out and starts sliding across horizantally really quickly and I can control it with my mouse. :(

I really like this Ubuntu so far, but this might hold me back from converting.

Hi and welcome, what is the model of the graphics card and have you installed the drivers? You can find the model by using the command lspci in the terminal located under applications, accessories. Look for VGA.
You may look for drivers under system, administration, hardware drivers.
You may also use the command with the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` and adjust there.

---

