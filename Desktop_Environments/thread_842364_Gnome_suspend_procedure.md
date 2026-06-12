---
title: "Gnome suspend procedure"
date: 2008-06-27
forum: Desktop Environments
---

### Post by Harry Muscle on 2008-06-27
Is there any documentation that outlines exact what happens when Gnome decides to suspend a machine.  The things I'm looking for is the actual commands that are run and any configuration files accessed that I can use to change these commands.  I need this info to start troubleshooting why my machine won't suspend when battery powered but will when AC powered.

Also, is it Gnome (via the Gnome Power Manager) that does the suspending or GDM (Gnome Display Manager).  Cause I found the GDM configuration file with the commands that are used, but then I read that when running Gnome the Gnome Power Manager takes over.  As a side note if anyone could explain the relationship of GDM and Gnome that would be highly appreciated.

Thanks,
Harry

P.S.  This is all on Ubuntu 8.04 running on a Dell Vostro 1000.

---

### Post by sdennie on 2008-06-27
In Hardy, the thing you are looking for is pm-utils and the commands you are looking for all start with pm-.  For example:

```

pm-hibernate       pm-powersave       pm-suspend-hybrid  
pm-is-supported    pm-suspend

```

The default configuration files can be found in /usr/lib/pm-utils and it's sub-directories.  You can add more functionality using the directories under /etc/pm.  Hope that helps.

---

