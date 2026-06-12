---
title: "Possible to change the boot order of GDM?"
date: 2009-06-16
forum: General Help
---

### Post by elektronaut on 2009-06-16
Hi,

I'm trying to have a script called during boot up. This script has to be executed after network is up but before GDM is started. Unfortunately the GDM start script has the link **/etc/rc*.d/S30gdm** and NetworkManager has **/etc/rc*.d/S50NetworkManager**. This order would have to be reversed, and my script started in between those two. So rc.local doesn't work, as it's executed in the end: **/etc/rc*.d/S99rc.local**.

Any idea what to do now?

---

### Post by sdennie on 2009-06-16
You can swap the order just by renaming those symlinks.  Things are executed in "alphabetical" order and neither of those two things are critical to start the system so, you could use:

```

S50gdm
S51your-script
S52network-manager

```

---

### Post by elektronaut on 2009-07-17
Thank you for your answer. I did the following a while ago:
```
cd /etc

cp -ax rc2.d/S50NetworkManager rc2.d/S30NetworkManager
rm rc2.d/S50NetworkManager 
*(same for /etc/rc[3-5].d/S50NetworkManager links)*

cp -ax rc2.d/S30gdm rc2.d/S34gdm
rm rc2.d/S30gdm
*(same for /etc/rc[3-5].d/S30gdm links)*
```
So that NetworkManager starts before GDM. Then I inserted a start link for my script in /etc/rc[2-5].d:
```
ln -s S33display-config ../init.d/display-config
```
So now the script is started after NetworkManager but before GDM. While the goal is achieved, I encountered a bug: **[COLOR="Red"]ACPI isn't working anymore[/COLOR]** :(

Is there something else than changing everything back to the original state I can do about that?

---

### Post by elektronaut on 2009-07-17
I no longer need the start script anymore as I found another way of achieving what I originally wanted. Would be interesting nonetheless to know how this could break ACPI.

---

