---
title: "Starting American McGees Alice from Gnome-Menu"
date: 2006-12-03
forum: Gaming &amp; Leisure
---

### Post by SleepyHollow on 2006-12-03
Hi Folks,

I bought Alice very cheap at the supermarket and gave it a try with wine and edgy eft. It works except for the mouse, but only with sudo or as root. :D I used the installation files of lifl.org named "alice_1.0-multilanguage.run" and installed it as root.

The starting command is "sudo runalice". I made a desktop luncher for it. 

Its a script (~/sbin/alice.sh) which contents the following lines:

#!/bin/sh
cat .FILE | sudo -S runalice

where .FILE is a file with the userpassword on a single line.

Now the problem: I have the alice-icon as a starter on the desktop with the entry "/home/myusername/sbin/alice.sh" and it works. But the same isn't working as entry in the gnome applications menu with alacarte. There is also no error message.

What can I do? I would like simply to understand this strange behavior. What is the difference between the two ways to start a shell-script via a starter on the desktop and via the gnome application menu?

Greetings,
SleepyHollow

---

### Post by edemark on 2006-12-03
Hi 
First I would suggest you to find a way of running your game as a normal user. As long as you do not NEED to run something as root do not run it as such. Only run something as root when it is needed. 
In reference to your question about the diference between the two ways of starting the game my guess would be that this is related to the sudo question . As far as i know sudo does not work from the gnome menu (unless you use the run something in a terminal option) i generally use gksudo (instead of sudo) to be able to gain super user privileges from the menu.

good luck

---

### Post by SleepyHollow on 2006-12-03
> **edemark said:**
> Hi 
First I would suggest you to find a way of running your game as a normal user. 
good luck

Nope. Its impossible. Only with root or sudo works this game in conjunction with wine.

> **edemark said:**
> Hi 
 As far as i know sudo does not work from the gnome menu (unless you use the run something in a terminal option) i generally use gksudo (instead of sudo) to be able to gain super user privileges from the menu.


It works now, I struggled alone some hours: I needed to give in the alice.sh the full path of all progs, like:


[B]#!/bin/bash
cat /home/myhomedir/sbin/.FILE | sudo -S /usr/local/bin/runalice[/B]


And this is strange but true: Do not enable the "run in a terminal"-option. Then it works.

I'm not a fond of this method to run a game as root. But if somebody has the answer how to start and run this game without root privileges at all then you are welcome.

:cool:

---

### Post by d3v1ant_0n3 on 2006-12-03
Heh. I couldn't even get this game to run in xp. It constatnly bugged out when doing the cd check, despite it being a fully legal copy. Might have to dig out the disc if it runs thru wine ok:D

---

### Post by anthro398 on 2006-12-04
> **SleepyHollow said:**
> Nope. Its impossible. Only with root or sudo works this game in conjunction with wine.


Uh, I run alice without root permissions.  'chown -R you /usr/local/games/alice'

---

### Post by SleepyHollow on 2006-12-05
> **anthro398 said:**
> Uh, I run alice without root permissions.  'chown -R you /usr/local/games/alice'

nice advice, thanks, do you have mouse support with alice?

---

### Post by anthro398 on 2006-12-05
Yes, I do.  I didn't go anything fancy to configure it.  I used an installer I got from I got from somewhere.  I could make it available to you, if you like. 
...

Oh, wait, come to think of it, I don't actually know if I have mouse support.  I'll check when I get home.  It seemed natural to me to play with the keyboard only.

---

### Post by SleepyHollow on 2006-12-08
alright I have the installer too, lifl.org, but really no mouse. If the game is totally playable without mouse than I will give it a try. Nevertheless it stays interesting if you have had mouse-support. Thanks for your efforts.

---

### Post by anthro398 on 2006-12-29
I do have mouse support.

---

