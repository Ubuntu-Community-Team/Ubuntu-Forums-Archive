---
title: "GDM Problems."
date: 2007-01-31
forum: Desktop Environments
---

### Post by eBait~ on 2007-01-31
Hello, I have a little problem here. It's about my GDM, which doesnt seem to work propertly, (meaning I can use it, but it seems to go in some other mode, giving me only the standard screen (gnome-gdm, not even ubuntu)).
When executing sudo gdmsetup, or gksu gdmsetup, I get this output.
```
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Kon het configuratiebestand van GDM niet benaderen.

``` Kon het configuratiebestand van GDM niet benaderen. = Dutch for "Coulnt read GDM's config file".
Also tried dpkg-reconfigure gdm several times with no luck. Logging out after reconfiguring seems to give a proper GDM. 
Some help would be nice. :) Thanks,

---

