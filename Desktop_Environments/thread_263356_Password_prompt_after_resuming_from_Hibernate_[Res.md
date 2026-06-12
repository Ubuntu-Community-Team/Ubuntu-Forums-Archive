---
title: "Password prompt after resuming from Hibernate [Resolved]"
date: 2006-09-23
forum: Desktop Environments
---

### Post by cnferntreegully on 2006-09-23
After reading some posts I have successfully enabled Hibernate to work my Dapper (yay!), thanks!

Just one thing - when it resumes back from Hibernate it always asking for password.  How can I remove this password prompt??

---

### Post by galileon on 2007-01-23
hello, i also would like to know how to do this! i have a HP TC1100 convertible pc, where the keyboard comes off when using it as a tablet.

trouble is, i need to connect the keyboard back to type the password if I am resuming from hibernation!

---

### Post by freshmint on 2007-01-25
I got the same problem :( 
would be really great to be able to deactivate this.

---

### Post by galileon on 2007-01-25
found it on another thread,

applications>accesories>terminal

type gconf-editor

go to the key at /apps/gnome-power-manager

look for lock_on_hibernate, disable it...theres one for suspend as well...

---

### Post by casaschi on 2007-01-25
Never tried this, but in the /etc/acpi/resume directory there is a collection of scripts that are run after resuming. One of them is something like ???xscreensaver or similar. It's executed at the end of the resume and fires up the screensaver with locked password.
You could look into that, or trying disabling it alltoghether by making it not executable.

Just a suggestion, there might be a straight switch to disable the password request, maybe in /etc/default/acpi-support or similar

---

### Post by freshmint on 2007-01-25
> **galileon said:**
> found it on another thread,

applications>accesories>terminal

type gconf-editor

go to the key at /apps/gnome-power-manager

look for lock_on_hibernate, disable it...theres one for suspend as well...
Thx that did it :)

---

### Post by groggyboy on 2007-04-07
> **casaschi said:**
> Just a suggestion, there might be a straight switch to disable the password request, maybe in /etc/default/acpi-support or similar

i was having trouble turning off the resume-from-suspend password feature with xscreensaver in xubuntu feisty.  as per your tip, i took a look in /etc/default/acpi-support.  about 3/4 of the way down, there was a line that reads like this:```
# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

```
i commented it out to look like this:```
# Comment this out to disable screen locking on resume
**#**LOCK_SCREEN=true

```

that solved the issue for me.  casaschi, thanks for pointing me in the right direction!

---

### Post by hotweiss on 2008-05-24
> **galileon said:**
> found it on another thread,

applications>accesories>terminal

type gconf-editor

go to the key at /apps/gnome-power-manager

look for lock_on_hibernate, disable it...theres one for suspend as well...

Thanks. I was looking for that.

---

