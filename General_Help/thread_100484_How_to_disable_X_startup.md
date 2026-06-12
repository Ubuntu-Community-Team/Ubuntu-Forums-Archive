---
title: "How to disable X startup ?"
date: 2005-12-07
forum: General Help
---

### Post by Bachstelze on 2005-12-07
I will soon get another comp I plan tu use as a server but I also want to be able to run a desktop manager if needed. So how do I disable X so I only get a command line at startup and run X manually if necessary ?

---

### Post by Pluk on 2005-12-07
sudo update-rc.d -f gdm remove

That will remove your startup links.

---

### Post by Bachstelze on 2005-12-07
thanks :)

---

### Post by speedman on 2005-12-07
It's worth noting that update-rc.d is primarily intended to be a developers tool for usage in scripts.  If you use update-rc.d to remove a start up symlink for a service the next time that package is updated the symlink will be recreated unless you create a K symlink in it's place.

To turn off gdm and keep it turned off after any updates to gdm you would use both of these commands:

update-rc.d -f gdm remove

ln -s /etc/init.d/gdm /etc/rc2.d/K13gdm


Regards,

SM

---

