---
title: "Reboot X from script"
date: 2007-03-20
forum: Desktop Environments
---

### Post by reillyp on 2007-03-20
I wrote a bash script that changes the Screen used in my ServerLayout section (via sed) and then calls **/etc/init.d/gdm restart** to supposedly restart my session - hopefully using the new Screen. This is so that I can add an item to my Xubuntu main menu that calls the script and my display toggles between my LCD monitor or my projector.

The problem is that **/etc/init.d/gdm restart** hangs - it stops with a black screen and an underline cursor looking thing at the top left. If I do alt+ctrl+F1 I get a tty login prompt and if I check out the processes, there is no gdm, xorg or anything in the list.

Anyone know how I can can restart the web server from a bash script called by a menu click? Note that I tried backgrounding the script call (putting " &" at the end of the command), but that made no difference...

Thanks.

---

### Post by digitzero on 2007-03-21
Instead of restarting it, you may want to try to completely kill gdm, and then start it clean.

```

sudo killall gdm
sudo /etc/init.d/gdm start

```

Does that work?

---

### Post by reillyp on 2007-03-21
That killed it all right - even alt+ctrl+f1, alt+f2, et al gave no response; short of ssh'ing in from my laptop had to hard-reset the computer... 8-[ 

Strangely, I tried using ps + grep + awk to get the pid for xinitrc and killed it - which acted exactly the way I wanted (seemed like I had pressed alt+ctrl+backspace) - BUT it did not re-read the xorg.conf file; instead it came up on the same Screen display... :confused: 

Unfortunately I'm new to the whole gdm concept - in my old gentoo setup I always booted to the tty and ran startx from the cli, so to toggle displays I just had a second ServerLayout in my xorg.conf and to use the projector just exited X normally and then ran "startx -- -layout projector"

---

