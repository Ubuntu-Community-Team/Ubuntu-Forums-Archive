---
title: "Start up script, before fstab"
date: 2009-04-06
forum: General Help
---

### Post by kripz on 2009-04-06
Where do i add start up commands before fstab is invoked?

---

### Post by drs305 on 2009-04-06
If by "before fstab" you mean during the boot process, you can put it in /etc/rc.local. Scripts in this folder run as root at the end of multi-user runlevels/bootlevels. Include the full path to whatever you want run.

If you want it to run only during a specific runlevel, it could go in a specific /etc/rc[COLOR="DarkRed"]X[/COLOR].d folder. In general, system processes (*Pre-logon*) are located in the /etc/init.d folder and run as root. The entries in /etc/init.d are referenced by the various /etc/rc.[COLOR="DarkRed"]X[/COLOR] folders whose contents are acted upon when the associated runlevel is called. The [COLOR="DarkRed"]X[/COLOR] is a number 1 through 6 associated with a runlevel.

So the actual process or script is placed in /etc/init.d and shortcuts to these are placed in the appropriate /etc/rcX.d. When a runlevel is called, each shortcut in the associated rcX.d folder is run. Shortcuts starting with "S" start something, those with K kill some process. The number following the letter (S99...) indicate the priority (0=high, 99=low).

You don't manually have to place the shortcuts in each rc.d folder. There are commands that automatically places/removes them in the folder(s) you specify.
```

sudo update-rc.d *scriptname* defaults # puts a start link in runlevels 2,3,4.5 & end link in 0,1,6
sudo update-rc.d *scriptname* start 99 2 3 .  # puts start link in runlevels 2,3 priority 99 (low), don't forget the "." at the end
update-rc.d -f *scriptname* remove	# removes links in rcX.d folders, not file in /etc/init.d

```

This probably doesn't provide the detail necessary to get a script working properly but should give you enough information to conduct a good search for how to write these scripts.

---

### Post by kpkeerthi on 2009-04-06
The OP probably wants to run something before the partitions are mounted.

---

