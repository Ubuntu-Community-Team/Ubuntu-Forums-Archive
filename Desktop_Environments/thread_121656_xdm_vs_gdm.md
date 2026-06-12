---
title: "xdm vs gdm"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Zelut on 2006-01-25
I installed server on my machine & use Xfce to have a super lightweight desktop, etc.  When I installed I included gdm for my gui login screen but I would like to try xdm.  I removed gdm & installed xdm but xdm doesn't start.  It tries but then just drops me back to the terminal.  Any ideas?

---

### Post by aysiu on 2006-01-26
Did you try ```
sudo nano /etc/X11/default-display-manager
``` and then editing it to be ```
/usr/bin/X11/xdm
``` instead of ```
/usr/bin/gdm
```?

---

### Post by Zelut on 2006-01-26
my file: /etc/X11/default-display-manager already reads

/usr/bin/xdm

but it doesn't load xdm at boot..

---

### Post by theunforgiven on 2006-02-19
i have the EXACT same problem.  Any solution yet?

---

### Post by jacob_lurch on 2006-02-28
[QUOTE=theunforgiven]i have the EXACT same problem.  Any solution yet?[/QUOTE]

I have the same problem too.  Anyone with good ideas on how to solve this?

Extra info:  even though xdm doesn't start on boot, issuing "startx" after a text login brings up xfce fine....so the X server appears to run ok.

---

### Post by draenor on 2006-04-19
Indeed I too have the same problem. It seems this is stacking up on alot of people. 

Also /var/log/X.org.0.log contains no obvious errors (there exist no xdm.log).

Just as the others, some info on this topic would be greatly appreciated.

---

### Post by blair on 2006-05-14
Add me to the list of folks trying to figure this out. I'd like xdm to auto-start on system startup and present a login screen. The basic question I believe is: how do you get xdm to automatically start. 

I'm trying to figure out if this should be part of system init, or part of my login (i.e. boot into a prompt). Different problems, likely requiring different solutions. Will post news if I figure it out.

---

### Post by Maelgwyn on 2006-05-15
From what I can see from the second post, the file shouldn't read /usr/bin/xdm! It needs to be /usr/bin/X11/xdm :)

---

### Post by TitusDalwards on 2006-05-15
what is the glossary of ~/.xinitrc file?
have u changed it to "exec start xfce"

---

### Post by Ludox on 2006-06-05
Hi,

Same question...

I would start XDM and graphical login on boot and start icewm after login...

---

### Post by Zed on 2006-09-14
xdm's starting for me. 

Look in /etc/inittab. You should have:

```

id:2:initdefault:

```

This is your default runlevel. Then do 

```

ls -l /etc/rc2.d/*xdm

```

The output should end with something like:

```

/etc/rc2.d/S99xdm -> ../init.d/xdm

```

As noted above, /etc/X11/default-display-manager should have as its entirety:

```

/usr/bin/X11/xdm

```

If all these things are true, and xdm's installed properly, so far as I know, it should start.

[An introduction to runlevels](http://www.debian-administration.org/articles/212)

To run icewm after login, one easy way is to put this in /home/username/.xsession:

```

#!/bin/bash
exec /usr/bin/icewm

```

(There are a lot of different ways one could achieve this.)

Updated: here's [another way.](http://www.debian.org/doc/FAQ/ch-customizing.en.html)

```

update-alternatives --display x-window-manager

```

If icewm is listed, then do:

```

update-alternatives --config x-window-manager

```

and select its number from the list you'll be presented. Otherwise do,

```

update-alternatives --install /usr/bin/x-window-manager x-window-manager /usr/bin/icewm 50

```

---

