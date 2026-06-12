---
title: "No keyboard input and window borders on second monitor"
date: 2011-06-11
forum: Desktop Environments
---

### Post by Pithikos on 2011-06-11
I run Natty 64x (new install) and have setup to use two seperate x servers and no xinerama. When I start my computer everything seems fine on both monitors but once desktop is loaded and I start an app in the second monitor, I can't type anything and the window borders are missing. If I type "DISPLAY:=0.1 metacity" the problem gets fixed but I get an error that a window manager is running already.

I have AMD/Nvidia, GeForce 8800GT.

---

### Post by Pithikos on 2011-06-11
It seems to work on gnome-safe mode but not otherwise

---

### Post by umerlone on 2011-06-19
I upgraded from 10.11 to 11.04 and I have the same problem.
Playing with NVIDIA X Server Setting I could get the keyboard responsive but trying to improve it I got back.
Now I have no idea how to make things work again.

---

### Post by birmasyd on 2011-06-20
Hi Guys,

I had the same problem and found a solution [here]("http://www.linuxquestions.org/questions/ubuntu-63/change-default-window-manager-to-metacity-752936/")

In summary:

Copy this to your clipboard:   metacity

Open a terminal on your working display (:0.0)

$ export DISPLAY=:0.1; gconf-editor

In the configuration editor that just opened browse to:
/desktop/gnome/session/required_components/

right click the 'windowmanager' key, edit and paste in the 'metacity' value you copied to clipboard earlier.

Logout of X and login in again.

success! (for me anyway.. hope it works for you guys)

---

### Post by rufwork on 2011-08-14
> **birmasyd said:**
> success! (for me anyway.. hope it works for you guys)

No luck here.  Man, that sounded good, though.  ;)

Hello, nurse:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/764051](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/764051)

DISPLAY=:0.1 compiz
... in the "working" monitor makes the windows wake up in the troublesome second.  I can type again.  Still can't share windows between monitors, but this will work.

---

### Post by geams13 on 2011-09-02
I was having the same problem.  A combination of the last two posts worked for me.  Changing the Window Manager of my non-working screen to metacity is what I needed to do, but I couldn't type in the gconf-editor to do it.  So first I ran this on my working monitor: 

DISPLAY=:0.1 compiz

That got my non-working monitor into a working state temporarily.  Then I ran gconf-editor on my non-working monitor (now temporarily working) and changed the windowmanager key to metacity.  Rebooted, and now I have two working monitors.  Good teamwork!

---

