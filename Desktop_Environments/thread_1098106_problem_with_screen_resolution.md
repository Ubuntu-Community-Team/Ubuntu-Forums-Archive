---
title: "problem with screen resolution"
date: 2009-03-16
forum: Desktop Environments
---

### Post by 3dz on 2009-03-16
Hi,
     I having a problem with screen resolution.  
A couple weeks ago, I was setting up my computer.  I've got the desktop effects to work, and I got the nvidia driver to work. I upgraded some of the programs, and loaded some video codecs.
 
 I got everything set up pretty good.  Then I shut it down for a couple weeks to reorganize.
 When I turned it back on, my screen resolution was stuck on 640 x 480.  I went to system/preferences/resolution settings  but the only option is: 320 x 240.  

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/pixels_slection.png[/IMG]

I had 800 x 600 pixel resolution before.  As an artist that was even hard to work with, but workable.
640 x 480, to me isn't workable. Can somebody tell me what's going on, and how to fix this. :(

---

### Post by taurus on 2009-03-16
Have you checked to see if you are still using nvidia driver for your graphic card?

Does your card show up in System -> Administration -> Hardware Drivers?

---

### Post by 3dz on 2009-03-16
Yes it's there, it says it's in use. I believe it's a restricted driver.

---

### Post by 3dz on 2009-03-16
Maybe this will help:

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/hardware_drivers.png[/IMG]

---

### Post by taurus on 2009-03-16
Can you post your /etc/X11/xorg.conf?

```
cat /etc/X11/xorg.conf
```
Also, the output of this command from a terminal.

```
lsmod
```

---

### Post by 3dz on 2009-03-16
Sorry it took so long, but you're about to see what I have to work with.  Everything is in order, right down the line

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/xorg_config1.png[/IMG]

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/xorg_config2.png[/IMG]

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/xorg_config3.png[/IMG]

and this is what I got back on the ls command.

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/lsmod1.png[/IMG]

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/lsmod2.png[/IMG]

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/lsmod3.png[/IMG]

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/lsmod4.png[/IMG]

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/lsmod5.png[/IMG]

man, I hope you're not on dial-up.

---

### Post by taurus on 2009-03-17
Make a backup copy of your /etc/X11/xorg.conf first

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```
and run either of these commands to configure your X server again.

```
sudo nvidia-settings
-or-
sudo nvidia-xconfig
```

---

### Post by 3dz on 2009-03-17
I really need to learn some commands. 
I copied the Xorg configuration.  It prompt me for my password. 
I entered my password, and once again I entered the copy command.
I've been entered the nvidia xconfig command.  It came back with two warnings.
At first, I didn't have a clue what it meant.  Then it hit me that it was talking about my keyboard and mouse.

I am in the process of setting up a two node network, for testing out software for render farm clusters.
I have a two port, USB KVM switch.  I have a generic USB keyboard with a two port hub, that I have
a wireless optical mouse connected to.
I am able to switch back and forth between the two nodes.

At the time, I didn't know what it was talking about.  So I entered the command for nvidia settings.
It came back: no command found.
I'm still stuck on the same resolution.
Now I am lost.  Not sure where to go from here.

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/x11_nvidia.png[/IMG]

---

### Post by 3dz on 2009-03-18
lol, I always seem to get myself into these computer situations.
I greatly appreciate your help!  Thank you! :)

---

