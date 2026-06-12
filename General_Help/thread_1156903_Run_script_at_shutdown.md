---
title: "Run script at shutdown"
date: 2009-05-12
forum: General Help
---

### Post by triplemaya on 2009-05-12
I'm following these instructions to run a script at shutdown.

if you want to add a script to the shutdown process then put the script in /etc/init.d and run "sudo update-rc.d NameOfScript stop 22 0 6" where "NameOfScript is the name of the script in /etc/init.d.
Then the script will be called as "/etc/init.d/NameOfScript stop" by the system (as root) on shutdown or restart.

When I do this I get this message

update-rc.d: warning: /etc/init.d/NameOfScript missing LSB information

which seems as if it might well work anyway, but I also get this message

update-rc.d: error: action with list of runlevels not terminated by "."

which suggests that it won't.

---

### Post by blackgr on 2009-05-12
inside the init.d the script files have a specific pattern under which they are written. Try editing another already installed script and see how it is written

---

### Post by triplemaya on 2009-05-12
Looking inside acpi-support there are just simple commands like

```
test -f /lib/lsb/init-functions || exit 1
```

The command in my script is simply

```
rm /home/pc/.thumbnails/*
```

There are two lines with a dot in front of them, whatever that means, eg

```
. /usr/share/acpi-support/power-funcs
```

There doesn't seem to be any special pattern in which they are written, what did you have in mind?

---

### Post by unutbu on 2009-05-12
I think all you need is to add a period to the end of the command:
```

sudo update-rc.d NameOfScript stop 22 0 6 .
```

---

### Post by triplemaya on 2009-05-12
thanks unutbu, works like a charm!

---

