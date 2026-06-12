---
title: "[SOLVED] Command Line For Shutdown GUI"
date: 2008-12-07
forum: Desktop Environments
---

### Post by jdorenbush on 2008-12-07
I am trying to figure out the command line for the Shut-down/Kill GUI.

```
/usr/bin/gnome-session-save --gui --kill
```

That command line only brings up the Log Off and Switch User dialogue. I am trying to get the dialogue that brings up Shut Down, Restart, Suspend, and Hibernate.

---

### Post by hictio on 2008-12-07
You have to type:

```

sudo /etc/init.d/gdm stop (ENTER)

```

Replace stop with start to enable again, this won't survive a reboot, if you want to do that, that is disable the GUI for a while, type this:

```

update-rc.d -f gdm remove (ENTER)

```

To re-enable, type this:

```

update-rc.d -f gdm defaults (ENTER)

```

---

### Post by jdorenbush on 2008-12-07
I am actually trying to apply it to an Applet in Avant.

Its actually basically what this guy asked for, but he didn't get much help

[http://www.linuxforums.org/forum/ubuntu-help/134836-shut-down-menu-command.html](http://www.linuxforums.org/forum/ubuntu-help/134836-shut-down-menu-command.html)

---

### Post by hictio on 2008-12-08
> **jdorenbush said:**
> I am actually trying to apply it to an Applet in Avant.

Its actually basically what this guy asked for, but he didn't get much help

[http://www.linuxforums.org/forum/ubuntu-help/134836-shut-down-menu-command.html](http://www.linuxforums.org/forum/ubuntu-help/134836-shut-down-menu-command.html)

I don't understand... The reply for what he/she asked its answered on the second post of that thread.

---

### Post by jdorenbush on 2008-12-08
I am trying to use a shutdown icon in Avant Window Navigator as an Applet. Not in the ubuntu Panel.

---

### Post by kawaji on 2008-12-08
```
gnome-session-save --shutdown-dialog
```

---

### Post by crazyness003 on 2008-12-08
> **kawaji said:**
> ```
gnome-session-save --shutdown-dialog
```
yup. that works
(crazyness approved!)

---

### Post by jdorenbush on 2008-12-08
> **kawaji said:**
> ```
gnome-session-save --shutdown-dialog
```

Thank you!

---

### Post by crazyness003 on 2008-12-08
please mark as solved in the thread tools. It will help other seeking the same answers; seek the answers...quicklier

---

### Post by jdorenbush on 2008-12-08
> **crazyness003 said:**
> please mark as solved in the thread tools. It will help other seeking the same answers; seek the answers...quicklier

I meant to do that, but I totally forgot. It is already marked as Solved though - maybe an admin did it?

---

### Post by crazyness003 on 2008-12-09
> **jdorenbush said:**
> I meant to do that, but I totally forgot. It is already marked as Solved though - maybe an admin did it?
its cool. dont think im pestering you, its just polite to let everyone know you fixed it. 
"sharing is caring and it can be more useful than windows"

---

### Post by glotz on 2008-12-09
**$ gnome-session-save --shutdown-dialog**
Unknown option --shutdown-dialog
Run 'gnome-session-save --help' to see a full list of available command line options.

---

### Post by crazyness003 on 2008-12-10
i think this only works for interpid. hardy still uses the old school one (dont remember what it was. maybe: *gnome-session-save --gui --kill* )

---

### Post by glotz on 2008-12-11
[QUOTE=crazyness003]i think this only works for interpid. hardy still uses the old school one (dont remember what it was. maybe: *gnome-session-save --gui --kill* )[/QUOTE]Confirmed, thanks.

---

