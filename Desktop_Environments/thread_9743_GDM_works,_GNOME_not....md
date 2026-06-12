---
title: "GDM works, GNOME not..."
date: 2004-12-31
forum: Desktop Environments
---

### Post by agu5tin on 2004-12-31
i have a weeiirddd problem with my fresh ubuntu install (i have some Debian experience).
The system starts, GDM starts working OK (no flinks on screen), but i have two problems:
1) The welcome sound makes kindda of a loop, it NEVER stops.
2) It lets me login, but the GNOME sessoin never starts, the screen stays blacks, but i still can see the mouse arrow (and move it around for that mathers).

I tried running GNOME directily from STARTX (i added to .xinitrc) but it wont start either.


I dont know what to do, any recomendations??.

The system es a VIA AllinOne system.

---

### Post by meneer on 2005-01-08
Same here!

However when I choose another session in GDM, Gnome instead of the default session, Gnome does start. But it's not ubuntu, it's lacking ubuntu menu's, icons and so on.

Any clue?

(standard athlon clone with nvidia)

---

### Post by taygan on 2005-01-08
make sure your home directory and all the files (including hidden ones) are owned by you.

---

### Post by meneer on 2005-01-08
Looks like they are all mine  :confused:

---

### Post by Uuranor on 2005-01-08
Have you an ethernet modem?
If yes turn off before log in Gnome and turn on after it is started.

---

### Post by meneer on 2005-01-08
Interesting :)
The system is not directly attached to a modem, it's on a switch behind an smeserver that's connected to the ethernet modem.

Login without network attached
- doesn't help.

I'll try booting without the network cable.
- No, no result

The system is connected via a kvm-switch, although the mouse is connected to the system itself (linux-kernel doesn't seem to like it, not an ubuntu problem).

---

### Post by Uuranor on 2005-01-08
Oh, I know my suggestion seems stupid, but I must do it if I want to log in gnome :P
I'm sorry if it doesn't work for you :(

---

### Post by Quest-Master on 2005-01-08
Try XFCE. It seems to work on every system, and is similar but much more lightweight than Gnome.

---

### Post by meneer on 2005-01-09
I just re-installed ubuntu. At least that's stable.

---

### Post by wallijonn on 2005-01-09
Can you boot with the Ubuntu LiveCD?

If so, you should be able to cd to the hda and edit /etc/inittab. Then change the init default level to 1 (line 5, change [COLOR=Blue]id:2:initdefault:[/COLOR] to [COLOR=Blue]id:1:initdefault:[/COLOR] then save the file, cd back to the CD and reboot without the CDLive cd.

This will bring you up in init default level 1. 
You would then log in, [COLOR=Red]cd /usr/X11R6/bin[/COLOR] and issue a [COLOR=Red]xf86config[/COLOR] or [COLOR=Red]xf86cfg[/COLOR] command. xf86config should start a text script and xf86cfg should start a video based config.

After you configure [COLOR=Blue]X[/COLOR] you would then issue a [COLOR=Red]startx[/COLOR] command.

You could always [COLOR=Red]cat /var/log/XFree86.0.log | more
[/COLOR] to see if you can gleam an inkling of what the problem may be.

---

### Post by meneer on 2005-01-10
Thank alot !

---

### Post by pocket on 2005-01-27
I'm having a similar problem, but mine starts only after I've logged in, and logged back out.  On the next login, my computer hangs with the same symptoms described before.   

I took a look at XFree86.0.log and found this interesting line that repeats for about 2000 lines:

(EE) R128(0): R128CCEWaitForIdle: (DEBUG) CCE idle took j = 0

What's it doing, and how do I break that loop?

---

