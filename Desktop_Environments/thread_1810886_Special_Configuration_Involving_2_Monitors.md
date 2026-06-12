---
title: "Special Configuration Involving 2 Monitors"
date: 2011-07-23
forum: Desktop Environments
---

### Post by N1GHTS on 2011-07-23
I am configuring a computer with Ubuntu Server and a basic installation  of Xorg. Currently the computer is configured to automatically log in,  open an Xorg session, and run a single full screen program. This  computer has a touch screen input and is made to do only one job.

At this point I am tasked to change the configuration to do something a  little more fancy. This is where I need some ideas on where to begin  this sort of configuration. 

What they want is to add a second monitor: a "read only" monitor with no user input. Like the touch screen monitor, it needs to run a distinct program in full screen as soon as it is started. To add to the configuration complexity, its a wide screen monitor that needs to be in portrait mode. 

So the trick here is to either launch two seperate Xorg sessions for each distinctly configured monitor with their distinct full screen program, or one big desktop where the same kind of thing can be accomplished.

The computer in question has an on-board video card as well as an Nvidia GeForce 210  card using proprietary nvidia drivers and it has 3 outputs (D-sub, DVI,  HDMI). I would rather use the nvidia graphics accelerator for both monitors,  but I can use the on-board as a fall back which I believe is an Intel  chipset.

Here is how I configured the auto-login / auto-start of just the single touch screen monitor.

```

sudo nano /etc/init/tty1.conf
    (Replaced line containing "getty" with this one)
    exec /bin/login -f USERNAME < /dev/tty1 > /dev/tty1 2>&1
sudo cp /etc/skel/.profile ~/
sudo nano ~/.profile
    (Added this to the end of the script)
    if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
        . startx
    fi
sudo nano /etc/X11/xinit/xinitrc
    (Here I put the program name I want to launch as soon as Xorg starts up)

```It works great! Now, how would I go about setting up the two monitor approach?

---

