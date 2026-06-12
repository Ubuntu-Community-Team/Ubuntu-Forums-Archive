---
title: "file managers - huh?"
date: 2005-04-17
forum: Desktop Environments
---

### Post by robert crowther on 2005-04-17
_1. Nautilus won't let me shunt files round the system 'Permission denied', or something like it._

Anyone enlighten me here? Is it that Nautilus is locked out of anything under home, for security reasons, or whatever? Is there any way of entering my superuser ID so that I CAN use a graphical front end while I'm shunting files round the system? Or is there a different GUI system I can use so that I can shunt files round, create directories, and the like?

And I suppose I'm asking to be overlooked, but this is also desktop related (see, efficient posting)...


_2. How do I launch xmbmon with my desktop?_

The full saga...

I wanted to monitor my cpu temperature

The most elegant method seemed to be to use Gkrellm. On the site, Gkrellm claims to read information from the mbmon daemon. Attempts to set the -P switches, on the two programs, with a neutral port (6500, derived from etc/services, I couldn't find 'nmap') failed.

Anyway, the Gkrellm site doesn't make it clear WHAT information it can read from the mbmon daemon, perhaps only sensors?

I set up gkrellm with lm_sensors, which worked first time.

Still seeking my CPU temp, I tried using xmbmon, with more success. But, strange, xmbmon will not execute from a gnome launcher. I also tried the 'startup programs' option under services, and it won't launch from there. I tried execution secondhand, using a one line shell script, and it won't launch from there either. The only way it executes is from a terminal...


Any light on either of these two?




Robert

---

### Post by Stormy Eyes on 2005-04-17
If you don't want to be restricted to $HOME, run **gksudo nautilus**.

---

### Post by az on 2005-04-17
1.  It is a unix file permissions thing.
2.  You can create a custom launcher on your panel.  Just right-click.

---

### Post by robert crowther on 2005-04-19
The nautilus trick is the one. Many thanks, because you've saved me no end of trouble. I was getting way tired of moving files by the command line.

This is the kind of problem new users run into. Even ones who read the manual.

Re: the xmbmon problem. I tried a desktop launcher - it was my first instinct that such a gadget existed. It was when this obvious, intended for the situation, solution failed that I posted. I've done a full reinstall since then (not for this issue alone!) and the xmbmon still will not launch from within the GUI.

It's a puzzle, that's for sure

---

### Post by az on 2005-04-19
Ideally, the package manager and administration tools should take care of anything outside of your home directory.  If you ever need to do anything that requires root priviledges, why use Nautilus?  There should be an easier way using synaptic or something else.

---

### Post by NaplesBill on 2005-04-19
[QUOTE=azz]Ideally, the package manager and administration tools should take care of anything outside of your home directory.  If you ever need to do anything that requires root priviledges, why use Nautilus?  There should be an easier way using synaptic or something else.[/QUOTE]

I did this little trick because it makes it easier to find and edit .conf files or similar tasks.  The "root terminal" is my favorite tool.

---

