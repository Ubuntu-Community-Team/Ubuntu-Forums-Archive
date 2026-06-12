---
title: "lid button won't suspend?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by naked on 2006-01-15
It seems to just turn off and lock the screen.

I've been looking for something that I can change, I even install gnome-power-manager and setup the preferences to suspend for the lid button... but nothing?

Help!

Thanks.

L (I have a Dell 700m w/ fresh install if that helps)

---

### Post by jasmuz on 2006-01-15
Have you tried this, located in the synaptic repositories:

hibernate - activates your computer's suspend functionality

---

### Post by naked on 2006-01-15
I tried that yes.  But my problem is not with suspending itself, I can do that fine via the 'logout' menu by choosing suspend.

But I cannot get the 'lidbtn' to suspend.  So my laptop won't suspend when I close the lid.

Anyone?

---

### Post by naked on 2006-01-15
Looking around I found '/etc/acpi/lid.sh'  which is called by '/etc/acpi/events/lidbtn'  All that lid.sh does is blank and lock the screen.

I changed this line in 'lidbtn' from :
action=/etc/acpi/lid.sh 

to this:
action=/etc/acpi/sleep.sh

Then 'sudo /etc/init.d/acpid restart' and tada!

L

---

### Post by rado_london on 2006-01-16
It worked for me. Thanks!

---

