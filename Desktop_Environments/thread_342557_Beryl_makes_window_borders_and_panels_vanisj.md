---
title: "Beryl makes window borders and panels vanisj"
date: 2007-01-20
forum: Desktop Environments
---

### Post by Jose Catre-Vandis on 2007-01-20
Hi Just installed beryl following the ubuntuguide instructions for an ATi card, I have an ATi 9550 installed and working well, with 3D AND direct rendering as required.

Installation went fine, and selecting XGL and logging in also fine.

My single panel (which I have at the bottom) at first appears as normal, but when desktop is finished loading it disappears. I have some folders on my desktop, double clicking allows opening but I have no title or status or side borders. Cannot Alt-F2 to get a dialog. Was able to track down to find the xterm exec, again no borders, and can run beryl-settings.

Only other thing, I have automatice login set up, so have to CTRL-ALT-BACKSPACE to get login and select XGL session. ( This shouldn't make any difference?)

Several reboots and logins have made no difference.

What else do I need to do to get things sorted?

Thanks  :(

---

### Post by astoltz on 2007-01-20
The current packages (0.1.99+0.2.0-beta1)  from the official beryl repository are pretty broken at the moment.  They are promising a new version soon and you might want to wait 'till beta2.

---

### Post by Jose Catre-Vandis on 2007-01-24
Got it going, needed to type beryl-manager in terminal then all the candy started to work :-)

---

### Post by medley on 2007-01-24
> **Jose Catre-Vandis said:**
> Hi Just installed beryl following the ubuntuguide instructions for an ATi card, I have an ATi 9550 installed and working well, with 3D AND direct rendering as required.

Installation went fine, and selecting XGL and logging in also fine.

My single panel (which I have at the bottom) at first appears as normal, but when desktop is finished loading it disappears. I have some folders on my desktop, double clicking allows opening but I have no title or status or side borders. Cannot Alt-F2 to get a dialog. Was able to track down to find the xterm exec, again no borders, and can run beryl-settings.

Only other thing, I have automatice login set up, so have to CTRL-ALT-BACKSPACE to get login and select XGL session. ( This shouldn't make any difference?)

Several reboots and logins have made no difference.

What else do I need to do to get things sorted?

Thanks  :(

Try this:

start a terminal session (ie konsole in kde)
type 'sudo nano /usr/bin/beryl-settings'

if you're using gnome, replace sudo with gsudo or whatever gnome uses.

Make sure the first line says '#!/usr/bin/python2.5'. It probably says '#!/usr/bin/python'

Then restart your X server. I hope this works for you. I spent a couple of weeks trouble-shooting Beryl. Once it runs, it's pretty nice. Enjoy.

---

### Post by Jose Catre-Vandis on 2007-01-25
Thanks medley

but opening beryl-settings (an executable) only gives me some gibberish in terminal (lots of @^@^@^ and A^A^A^ and so on). I am in Gnome.

---

### Post by dabl on 2007-01-25
Something is wrong with your installation.  The command "beryl-settings" in the console should bring up a graphical settings window.  I advise removing and re-installing Beryl.

---

### Post by Jose Catre-Vandis on 2007-01-27
> **dabl said:**
> Something is wrong with your installation.  The command "beryl-settings" in the console should bring up a graphical settings window.  I advise removing and re-installing Beryl.

It does as you say, but I cannot "edit" beryl-settings" in terminal.

Everything works fine once I run beryl-manager in terminal.

Now lots of beryl questions:

How do I run beryl-manager automatically at login to the XGl session?
Do I simply put it in start up programs? But I guess it should only run for the XGl session?
(resolved - placed beryl-manager in startxgl.sh)

Also is the "3D Effects" plugin available for Dapper, doesn't seem to appear in the beryl-settings list?
(the one that makes see through cube and layers the windows)

Also Beryl does not recognise my "Super" key, If I type it into one of the keyboard change boxes it comes up as "Super_L"?

---

