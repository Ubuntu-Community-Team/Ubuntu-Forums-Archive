---
title: "not shutting down properly on kde"
date: 2007-06-27
forum: Desktop Environments
---

### Post by Trogdor 20X6 on 2007-06-27
I recently installed kubuntu-desktop and switched from GDM to KDM. Whenever I try shutting down while I'm logged in with KDE my monitor will turn off and my computer will just hang until I hold down the power button and force it to turn off.

The only time it shuts down is if I log out first then shutdown, shutdown from a gnome session, or if I use use sudo poweroff, halt, or shutdown. It only seems to hang when I shut down while logged in with KDE.

Does anybody know what's going on with KDE that is keeping it from shutting down?

---

### Post by Soimafreak on 2007-06-28
Not sure if this will help or not but..

[http://www.linuxforums.org/forum/peripherals-hardware/4389-shutting-down.html](http://www.linuxforums.org/forum/peripherals-hardware/4389-shutting-down.html)

I've had the issue before but I can't remember how I solved it. 

I suggest you try opening a terminal and type the following.

```
sudo shutdown -h now
```

The -h option does 1 of 2 things either power off or just halt (like yours is currently doing)
If you wish to force a power off do ... 

```
sudo shutdown -P now
```

That should shut down your computer and turn it off. If you do "man shutdown" you'll see there's a lot of options and powering off (halting) is one of them.

---

### Post by mukherjee.siddhartha on 2007-10-14
Same here, "sudo poweroff" also works but only from terminal.
Any idea on how to fix this for the GUI/Shutdown button ?

---

### Post by mukherjee.siddhartha on 2007-10-14
I  dont remember in which url i found it, but this worked for me fine.

"TerminateServer=true"

Add this in the [X-:*-Core] section of the kdmrc-File (/etc/kde3/kdm/kdmrc) - beware of the ':', there is a similar named section without the ':'.

---

