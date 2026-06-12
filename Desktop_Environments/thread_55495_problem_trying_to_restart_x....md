---
title: "problem trying to restart x..."
date: 2005-08-09
forum: Desktop Environments
---

### Post by dingobiatch on 2005-08-09
im having problems when i try to restart x. i have been told to hit ctrl-alt-backspace.
this problem started when i reconfigured xserver to use my 1680x1050 resolution.
now, before i installed my drivers, i still had something wierd going on *i think*.

before i installed my nvidia drivers, i would hit ctrl-alt-backspace and x would quit, but i would get a command line instead of x starting up again. was this normal?

now, for the real problem: since i have installed my nvidia drivers, i hit ctrl-alt-backspace, and my screen goes black like its going to that command line, but nope, monitor stops getting signal (like computer is off). now, if i hit ctrl-alt-backspace again, the monitor turns back on, but the screen is black. ill hit keys and nothing happens, and ive waited for a while, nothing happens. then it just repeats if i hit ctrl-alt-backspace again, monitor off again. ahh!
the only thing i can do from here is press the power button on my comp, and then it goes to console and it shows the command line as if im about to type something in, and after 5 seconds of freezing up, it just turns off.

any ideas?

---

### Post by az on 2005-08-09
You can do CTRL-ALT-F1 and log into the terminal.

do

sudo /etc/init.d/gdm stop

sudo dpkg-reconfiigure xserver-xorg

and when it asks about monitor, pick medium and take something like 1680x1050 at 60 Hz, to be conservative. and then

sudo /etc/init.d/gdm restart

---

