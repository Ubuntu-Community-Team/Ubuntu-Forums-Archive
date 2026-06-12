---
title: "Halp! No GUI on startup!"
date: 2007-06-15
forum: Desktop Environments
---

### Post by andycyca on 2007-06-15
Hi everyone

Last Night I upgraded my xubuntu to 7.04, and shut the system down normally. This morning I woke, started up, worked a little and tried to shut down the pc, but it asked me for a password. I put my password *the same I use foe Synaptic and such( and it told me that my account didn-t have the permissions to shut down. I logged off and then the screen went as if it was trying to shut down. It was like this for 10 min and then nothing. Now I tried to start again and just after the xubuntu bar fills, then the *Starting up...* and there-s a message saying that there-s some problem with my graphical interface for X or something. It asks me to show a diagnose of the problem, but I can-t figure out anything.

Help! I-m writing from my 6.06 live cd.

---

### Post by Happy_Man on 2007-06-15
Were you using Envy drivers?

---

### Post by andycyca on 2007-06-15
I have no idea (sorry) Is there any way I can know **(question mark)** I can say that this PC was meant for Win98, so it-s pretty old now.

---

### Post by Happy_Man on 2007-06-15
Which means you weren't..... (you would know if you had installed Envy). Ok, keep pressing enter on the error screens until you are dropped to a fullscreen terminal. Log in, and then type 
```
sudo dpkg-reconfigure xserver-xorg
``` Choose all the defaults until you get to the list of drivers. Scroll to select "vesa", spacebar to select, enter until you finish. Then type ```
sudo /etc/init.d/xdm start
``` Everything should work. Post back with any problems.

---

### Post by andycyca on 2007-06-16
Seems to work. The only strange thing is that the terminal didn't recognize my admin account (even with the sudo O_o) but logged as root no problem

Thanks a lot Happy_Man! You really saved my life.

---

### Post by muymalestado on 2007-07-03
And ?  When sudo dpkg-reconfigure xserver-org returns the information that xserver is not installed where do we look?

Thanks

---

### Post by Happy_Man on 2007-07-03
Did you do a server install? If so, run the command ```
sudo apt-get install ubuntu-desktop
```

---

