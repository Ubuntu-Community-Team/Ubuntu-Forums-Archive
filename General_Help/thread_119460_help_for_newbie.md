---
title: "help for newbie"
date: 2006-01-19
forum: General Help
---

### Post by ritch_Texas on 2006-01-19
I am new to linux and have just downloaded umbuntu on an HP machine
with no network card......the software starts...prompts for user and password...then sits there with a ~$ prompt...what am i doing wrong...that the os isn't loading....:confused:

---

### Post by MJSOnline on 2006-01-19
Are you in the "terminal" window?
Matthew

---

### Post by bulldogzerofive on 2006-01-19
Um, you might want to be more specific.

First of all, the OS (that is such an undescriptive term) has loaded and is running.  The kernel is running and you have logged into text based user environment (shell) called bash, which is waiting for you to tell it to do something.  Try typing "sudo init5" or "startx."  The problem that you are having is that the graphical user interface did not start, as it was supposed to.

So, to help us help you please let us know more precisely what you have done and seen.

For example, you downloaded a CD.  Is is the live CD or the install CD?  How did you install the operating system?  Did you use all the defaults or did you customize things?  Do you get any error messages during the boot or does everything check out "OK" as it scrolls by?  When you get the prompt are you on a new blank screen or is the leftover text from the boot still there?  Is the machine old? Does it have enough RAM?  What version of Ubuntu are you trying to run?

Be sure to check back with us (even if you fix it post how you did so that people with your problem in the future can see your solution) and Good Luck!

---

### Post by pbb on 2006-01-19
I also have this problem *sometimes*, I just get a terminal username prompt after booting. I enter my credentials and type startx to start Gnome. Next time, everything works fine again. I haven't found any regularity in it yet.

---

