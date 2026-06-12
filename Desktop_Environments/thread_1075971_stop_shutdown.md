---
title: "stop shutdown"
date: 2009-02-20
forum: Desktop Environments
---

### Post by gishaust on 2009-02-20
hi ubuntu fans

I have a bit torrent I am trying to download. My issue is every time I leave the computer it shuts down after a while. How do I stop this?

gishaust

---

### Post by sharathpaps on 2009-02-20
hi, there are options in the torrent client to automatically shudown after a download is completed. Have you set up anything like that? What torrent client are you using on what distribution of Ubuntu?

---

### Post by gishaust on 2009-02-20
transmission

---

### Post by yther on 2009-02-20
It's possible you could have some kind of power management setting kicking in, that is shutting down because the keyboard and mouse have been idle.  Have you checked for that sort of thing?

---

### Post by gishaust on 2009-02-20
how do I do that?=)

I have looked under keyboard and there seems to be nothing that would do that!

---

### Post by vginov on 2009-02-20
Change your power Manager Setting 

I guess mostly that would be the problem.

Change the idle time and auto shutdown options 

to do that go to System > Preferences

---

### Post by yther on 2009-02-20
In KDE, the applet is called "kpowersave," but I'm not sure if you are on Gnome.  Perhaps if your application menu/launcher has a search function, type in "power" and see what happens.  :)

---

### Post by gishaust on 2009-02-20
I have found the power management tool and it is set to never shutdown and never suspend. Yes I am using gnome

---

### Post by gishaust on 2009-02-20
I have been look through the logs 
gnome-power-manager:(server) suspending computer. Reason: System idle.

---

### Post by gishaust on 2009-02-20
If I shut down the gnome-power-manager will the system still keep working.

---

### Post by gishaust on 2009-02-21
I have a fixed the problem by sudo kill all gnome-power-manager. I have been going for over three hours and it has not been an issue.

---

### Post by Return Privacy on 2012-07-11
Hi, I installed "powerpanel for linux" from cybersystems on Ubuntu 11.10 tonight.
The problem is that now, as soon as the computer boots up, it IMMEDIATELY shuts down!
I don't have the UPS even attached to the computer, the computer is still plugged into 
the wall. I know how to issue the remove command to uninstall the new software, 
it's    dpkg -r powerpanel   
but, I can't get the bleeping computer to stay on long enough to do anything? It fully boots up
as normal, and as soon as the desktop screen comes up, it does a shutdown. I know it is the stupid
new software that changed something. 
Is there any way to stop the shutdown when it boots up? I need to be able to open a terminal and uninstall this software.....
I would REALLY appreciate any help with this one. :confused:

---

### Post by Return Privacy on 2012-07-11
Hi again,
I found a solution to my problem. I turned on computer, and immediately after Bios screen, pressed "shift" button, and it gave me the Grub screen to choose normal boot or Recovery Mode. I chose Recover Mode, and then it gave me the option to start with a command line. I did that, logged in, and then issued the remove command for the "powerpanel" software. Then I re-booted and it solved the problem. 
I am going to be sending Cybersystems an email advising them that their "Powerpanel for Linux" .deb package software has some issues! 

At least my part of this question is resolved....whew!....:D

---

### Post by wildmanne39 on 2012-07-11
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

