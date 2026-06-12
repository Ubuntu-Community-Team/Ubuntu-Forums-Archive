---
title: "Inspiron 6400 touchpad problems"
date: 2010-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Moooca on 2010-06-16
Hey everyone

This is an old bug, hasn't been solved

**[SIZE=3]"Synaptic  touchpad fails to register some of the taps for tap-to-click"[/SIZE]**


[https://bugs.launchpad.net/debian/+source/xserver-xorg-input-synaptics/+bug/133060](https://bugs.launchpad.net/debian/+source/xserver-xorg-input-synaptics/+bug/133060)


I think the problem is very clear from the bug report
(When using tap-to-click, the synaptics driver fails to register some  taps as clicks. I have managed to link this with abnormal coordinates  reported by the driver using "synclient -m 10". Whenever a tap is not  registered as a click, there is one or more consecutive reports of  touching at coordinates (x=1, y=5855), which might explain why it is not  registered as a click.)

It's not a matter of sensetivity, but it's strange that some taps are recognized others are not

anyways, I tried to go around this issue but I couldn't
the problem exist since 2007 till today

btw, the problem exists on all distros I've tried ( ubuntu - fedora - suse - pclinux )

if anyone can help me I'll be thankful 

----
As the last solution, I was thinking of replacing the synaptics driver
I think there is an alternative called "Alps"
[http://www.medini.org/software/alps/alps.html](http://www.medini.org/software/alps/alps.html)
but I don't know how to install it :(

---

### Post by Moooca on 2010-06-17
:lolflag:

Sorry , I posted before seeing the update in the bug report
because I struggled with this issue for over 2 years I though it will never be solved

the solution is

```

1. apt-get source xserver-xorg-input-synaptics
2. sudo apt-get build-dep xserver-xorg-input-synaptics
3- modify the file in the home folder/xserver-xorg-input-synaptics-1.2.2/src/synaptics.c 



just after the line 2090 where it says:
  Bool inside_active_area;
  /* update hardware state in shared memory */
 if (shm)
 {
    shm->x = hw->x;
    shm->y = hw->y;
    shm->z = hw->z;
 ...
 Now it should look like:
     Bool inside_active_area;
     if (hw->x == 1 && hw->y == 5855)
    {
        hw->numFingers = 0;
        hw->fingerWidth = 0;
        hw->z = 0;
        hw->x = HIST(0).x;
        hw->y = HIST(0).y;
    }
     /* update hardware state in shared memory */
    if (shm)
    {
        shm->x = hw->x;
        shm->y = hw->y;
        shm->z = hw->z;

4. save & close the file
5. sudo dpkg-buildpackage

6-log out  or restart X

```
btw, this is for lucid
I'm using 64bits, I don't think there will be much difference than the 32

---

### Post by jbrice on 2010-12-21
My recipe to get the Inspiron 6400 touchpad to work reliably with Lucid is to add the following code (needs Alt+F2 then "gksu gedit") to the end of this file
/usr/lib/X11/xorg.cong.d/10-synaptics.conf:
> Section "InputClass"
Identifier "touchpad catchall"
MatchIsTouchpad "on"
# Bodge to make tapped clicks work reliably on Inspiron 6400
Option "LBCornerButton" "1"
EndSection

Then reboot. 

To check if it's working, use "synclient -l" in a terminal window then look at the output and check that "LBCornerButton" has a value of "1".

This is maybe not the best place to put his code - am open to advice from the experts.

The explanation of why this works is in here:
[https://bugs.launchpad.net/debian/+s...cs/+bug/133060](https://bugs.launchpad.net/debian/+s...cs/+bug/133060)

---

