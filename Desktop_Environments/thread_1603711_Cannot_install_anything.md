---
title: "Cannot install anything?"
date: 2010-10-23
forum: Desktop Environments
---

### Post by Tehsimpl on 2010-10-23
I was trying to install something one day, I cannot remember what it was. But I ended up deleting a lock file somewhere and doing something to another file. But not I cannot install anything anymore?

[http://i52.tinypic.com/xgb21l.png](http://i52.tinypic.com/xgb21l.png)

Thats a screenshot of what I get once I try to, I was testing it with VNC, but it does the exact thing with anything U try and install? It also will not update anything aswell and I need to be able to install stuff for school aswell.

Thanks, and please reply asap. UBUNTU ftw!

---

### Post by sikander3786 on 2010-10-23
As the terminal mentions in the error output, try

```
sudo apt-get install -f
```

And post the output here. Don't post a screenshot, just copy/paste from terminal.

---

### Post by Tehsimpl on 2010-10-23
I don't fully understand what just happened? Lol

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  tk libvncserver0 tcl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tcl
The following NEW packages will be installed:
  tcl
0 upgraded, 1 newly installed, 0 to remove and 122 not upgraded.
Need to get 4,154B of archives.
After this operation, 69.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main tcl 8.4.16-2 [4,154B]
Fetched 4,154B in 0s (15.5kB/s)
Selecting previously deselected package tcl.
(Reading database ... 151964 files and directories currently installed.)
Unpacking tcl (from .../archives/tcl_8.4.16-2_all.deb) ...
Processing triggers for man-db ...
Setting up tcl (8.4.16-2) ...
update-alternatives: using /usr/bin/tclsh-default to provide /usr/bin/tclsh (tclsh) in auto mode.

```

---

### Post by sikander3786 on 2010-10-23
> I don't fully understand what just happened? Lol

I don't see any error message in that output. Can you confirm if it is solved? Try to install some other software and see if it is successful.

Also, you have got un-needed packages. You can remove them by (if you want to, no harm if they are left there, it will just free up some 'little' space)

```
sudo apt-get autoremove
```

---

### Post by Tehsimpl on 2010-10-23
O.o, can I REP?

---

### Post by sikander3786 on 2010-10-23
> **Tehsimpl said:**
> O.o, can I REP?
What, Can't understand?

---

