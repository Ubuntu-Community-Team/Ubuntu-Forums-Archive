---
title: "Time settings difference in windows and Ubuntu"
date: 2009-05-14
forum: General Help
---

### Post by Extol11 on 2009-05-14
Hi! I have two hard drives inside my machine, one for Ubuntu and one for Windows. I noticed that when I use Ubuntu, it displays the time correctly but it seems it changes something in the bios clock (the only explanation I can think of) and the windows says the time is four hours ahead of what it really is. In older Ubuntu versions and in OpenSuse I remember finding an option to tell the OS to use the time stored on the bios or something like that. Then both Operating systems would show the time correctly and I would not have to keep telling windows to sync with time.windows.com . Can anyone tell me how to do this in 9.04? Or if there's a work around for this? I have the time set to Puerto Rico in Ubuntu and Caracaz, la Paz in windows. It's gmt-4. Thanks in advance

---

### Post by mdurham on 2009-05-14
gksu gedit /etc/default/rcS and set UTC=yes or UTC=no according to how you want it to be.
Cheers, Mike

---

### Post by Extol11 on 2009-05-14
Thank you. But is there a GUI way of doing that?And what causes windows to interpret the time one way and Ubuntu another?

---

### Post by mcduck on 2009-05-14
> **Extol11 said:**
> Thank you. But is there a GUI way of doing that?And what causes windows to interpret the time one way and Ubuntu another?

If you have that setting as "yes", Ubuntu assumes your CMOS clock uses UTC time (which would be the default behavior for all Unix systems). Windows, however, assumes that CMOS clock runs in local time. So you need to change that setting to "no" to make Ubuntu consider CMOS time as local time as well.

---

### Post by Dngrsone on 2009-05-14
> **Extol11 said:**
> Thank you. But is there a GUI way of doing that?And what causes windows to interpret the time one way and Ubuntu another?

The GUI way to do it is to open a terminal and type in or paste the following command as Mike suggested:

```
gksu gedit /etc/default/rcS
```

That will open up a nice, shiny GUI text editor where you can find the term UTC=yes and change it to UTC=no (don't forget to save).

---

### Post by Extol11 on 2009-05-14
Thanks a lot for your help, guys. I'll do it as soon as I get home.

---

### Post by Extol11 on 2009-05-14
> **Dngrsone said:**
> The GUI way to do it is to open a terminal and type in or paste the following command as Mike suggested:

```
gksu gedit /etc/default/rcS
```

That will open up a nice, shiny GUI text editor where you can find the term UTC=yes and change it to UTC=no (don't forget to save).

Already did it. Thanks!

---

