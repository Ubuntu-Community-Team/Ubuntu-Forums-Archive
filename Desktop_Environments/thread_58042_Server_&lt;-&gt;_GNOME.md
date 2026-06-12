---
title: "Server &lt;-&gt; GNOME"
date: 2005-08-18
forum: Desktop Environments
---

### Post by mioip on 2005-08-18
I installed Ubuntu for desktop to ease setup. Is it now possible to boot into a server mode, as old Windows versions had the option to boot into a command-line mode and turn on the desktop environment from there?

Or, an even better question, would this have any practical application as far as performance goes?

---

### Post by jmlude_93 on 2005-08-18
i'm new to linux, so someone else might be of more help than I, but if you're trying to boot Ubuntu into a command line without starting X, then:

cd /etc/rc2.d
mv S13gdm no.S13gdm

as long as you change S13gdm to something else, the system won't automatically boot the graphical login screen, and instead it will boot into tty1

you have to be sudo to do this, and you can always change it back if this isn't what you're looking for

---

### Post by schdefan on 2005-08-18
What do you mean exactly with server mode?
If you don`t want to run X server you can delete the startup entries in /etc/rcN.d by using 
```
update-rc.d -f <program> remove
``` 
or the hard way uninstall X, gnome and gdm.

With ```
update-rc.d <program> defaults
``` you can start your program at boottime.

Hope that is what you meant.
schdefan

---

### Post by mioip on 2005-08-18
By server I mean the command line bash... ie if you were to install Ubuntu in "server mode."

I was looking for a way to say, "Ok, now I'm working in GNOME, now I want to restart my computer and it would load the command line, not GNOME. After I run it like that, if I want to play around in a GUI I can restart GNOME."

I don't really want to delte GNOME, since I intend to use it.

---

### Post by Carpe Libertatem on 2005-08-18
[QUOTE=mioip]By server I mean the command line bash... ie if you were to install Ubuntu in "server mode."

I was looking for a way to say, "Ok, now I'm working in GNOME, now I want to restart my computer and it would load the command line, not GNOME. After I run it like that, if I want to play around in a GUI I can restart GNOME."

I don't really want to delte GNOME, since I intend to use it.[/QUOTE]
 I was wanting to do the same thing earlier, and someone in the IRC room was kind enough to help me. Here's what I did:

installed rcconf (apt-get install rcconf)
ran from rcconf shell 
select gdm, hit space, enter, you're done!

Very simple I'd say, and you can still start Gnome whenever you need to.

---

### Post by Ptero-4 on 2005-08-18
[QUOTE=Carpe Libertatem]I was wanting to do the same thing earlier, and someone in the IRC room was kind enough to help me. Here's what I did:

installed rcconf (apt-get install rcconf)
ran from rcconf shell 
select gdm, hit space, enter, you're done!

Very simple I'd say, and you can still start Gnome whenever you need to.[/QUOTE]
 The easy trick for me is to delete the gdm entry from the rc3.d part, reboot (on redhat and debian system runlevels can only be updated at boot, gentoo have a custom tool for updating runlevels, but AFAIK it only works in gentoo b/c the runlevels in gentoo are custom tailored and not the regular type.). and use init 3 when you want to turn X11 off and init 2 to start X11 up again (need root privileges for running init 3 and init 2).

---

