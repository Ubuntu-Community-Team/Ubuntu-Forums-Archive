---
title: "Inspiron 1100 Lid Close - Reopen Problems"
date: 2008-10-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by csy33delight on 2008-10-01
I have installed Hardy on an Inspiron 1100. When I close the lid, the screen blanks and does not come back when it is reopened.

What I know so far:
Testing in lid.sh
When Power Management is set to Blank Screen, lid.sh exits at CheckPolicy.
When Power Management is set to Do Nothing, lid.sh executes (properly?) on both open and close but seems to have no effect.
Neither case seems to have any effect on the problem.
I am currently running with lid.sh patched to exit immediately without executing. Power Manager is set to Do Nothing.

When the lid is closed, the screen is shut off. When the lid is reopened, the screen flashes the desktop briefly (1/2 sec) and then goes black. Everything appears to be running [Ctl][Alt][Del] then [Alt]S causes the laptop to shutdown.

Nothing that I have tried so far seems to have any effect. I have been searching and testing for the last few days to no avail.

Does anyone know the path that is taken from the hardware event to action?
How does ACPI and Power Manager interact? Are there other Ubuntu programs that could shut off the display on lid closure?

I have been working with ubuntu for only 6 months. I have a Inspiron 5100 running Gutsy which works OK, and a Inspiron 1150 running Hardy which has lid closure issues also.(It appears to lockup when the lid is closed, but I will assault it after I fix the 1100).

Thanks, any help would be appreciated.

---

### Post by frag85 on 2008-10-29
with ibex 8.10 the screen no longer dims, but power management does not seem to take place. the screen will shut off after the specified time, and come on when the system is no longer idle, i can put the computer to sleep (suspend to ram and HDD) and it comes back OK, but none of these will happen on their own; after the set time period, except when the battery is critical. seems the same on both my inspiron 1100 and 1150.

---

### Post by scarf on 2008-12-26
i have installed 8.10 but am having similar issues to what csy33delight describes.  for example, the power management is activating properly (automatically and manually).  however, when coming out of suspend or hibernate, the display remains off (back-light is off).

i stumbled upon _[this thread](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-08/msg00402.html)_ which explains a successful work-around.

after resuming from standby or hibernate, i have switched to tty1 and issued the command (prepended with sudo), and the display will turn back on, and i can switch back to tty7.

now, the second part is to automate this command upon resuming from standby/hibernate, by supposedly editing the /etc/defualt-acpi-support.  Marius was less than generous in explaining *where* to edit within this file.  can anybody shed some light?

---

### Post by scarf on 2009-01-09
bump

---

### Post by scarf on 2009-01-27
:confused:

anyone know how to automate the command "vbetool post" by editing the /etc/default/acpi-support, as explained in the post i linked to previously?

---

