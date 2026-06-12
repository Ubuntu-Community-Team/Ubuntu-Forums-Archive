---
title: "lots and lots of desktopcouch processes"
date: 2011-05-14
forum: Desktop Environments
---

### Post by dr_saaron on 2011-05-14
For one of the user IDs I noticed the last the couple of days there are a ton of /usr/lib/desktopcouch/desktopcouch-service processes running.  I counted over 200 last night.  And some of those processes are maxing out a CPU.  But it's not for all user IDs.  Any idea what could cause that?

---

### Post by dr_saaron on 2011-05-15
I've had to write a simple script to periodically kill all that user's desktopcouch-service processes, which seems to have some side effects like not being able to switch users from the main logon screen.  

All the processes are orphans, so I can't see what is spawning them.

---

### Post by dr_saaron on 2011-05-15
OK, it seems to have had something to do with indicator-weather.  I uninstalled that and do not appear to be having any issues now.  I don't know if it's just because that's the only thing that uses desktopcouch that I'm currently running, and thus a problem there, or with the indicator.

---

### Post by mesocool on 2011-06-13
> **dr_saaron said:**
> OK, it seems to have had something to do with indicator-weather.  I uninstalled that and do not appear to be having any issues now.  I don't know if it's just because that's the only thing that uses desktopcouch that I'm currently running, and thus a problem there, or with the indicator.

removing indicator-weather does solve the problem.

---

