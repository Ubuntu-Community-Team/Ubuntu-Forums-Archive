---
title: "GUI won't start"
date: 2013-03-19
forum: Desktop Environments
---

### Post by Habermas on 2013-03-19
Hello!

Recently I've had some problems with my Ubuntu 12.04. The desktop used to become unresponsive from time to time. There were lines and stripes on the screen. It always happened quite randomly, I was just browsing the internet and BAM the computer goes all crazy, the desktop becomes flaky, etc. 

At those times I just rebooted the computer until it magically fixed itself, sometimes I had to reboot more than once. I tried the recovery mode, tried to fix packages, etc. While I tried to load fail-safe desktop environment I noticed that there was an error - "KVM disabled by BIOS", so I looked for solutions, and the best I could find was to enable virtualization in my BIOS settings, which I did. 

Now the problem is that Ubuntu does not boot into GUI, all I get is black screen with information on what processes are running. I can switch to console (ctrl+alt+F1) and when I switch back to GUI (ctrl+alt+F7) I still have that black info screen. 

Screenshot of the black screen I'm getting when booting: 

[http://ubuntuone.com/2WoUggAh3gND7yANjiARcr](http://ubuntuone.com/2WoUggAh3gND7yANjiARcr)

Thanks in advance :)

edit: After a forced shutdown I've managed to get back into GUI, but I'm hoping that there might be someone out there who has encountered similar issue and has managed to come up with a solution :)

---

### Post by Bashing-om on 2013-03-19
Habermas; Hi !

A number of things pop to mind.
1. Over heating: How long since you blew the box out ?
2. Physical seat of the graphics card: (also dust related), have you tried reseating the card ?
3. Graphics card driver: Have you tried (Additional Drivers utility) installing a different driver ?
4. Ever looked at the log files to see if there is an indication of a fault ?
5, Depending on what all was changed in bios. Might consider resetting to defaults. 
[INDENT=2]
good places to start

[/INDENT]

---

### Post by Habermas on 2013-03-20
Thanks for your response Bashing-om! The computer is running well at the moment and I think you might be right about this issue being dust-related cause it's been like 2 years since I've cleaned the box and for all this time it has been missing one of the sidelids. I better clean it :)

---

### Post by Habermas on 2013-03-29
Sorry for double-posting, I just need to revive this topic because the issue has become relevant again. I cleaned the computer, changed the thermal paste and it was running just fine for a couple of days, and now it happened again - can't boot into graphical interface. 

I get the Ubuntu loading screen but it has some weird blue lines accross it (picture: [http://ubuntuone.com/71hUhe7RU35bWsHOVx6rUC](http://ubuntuone.com/71hUhe7RU35bWsHOVx6rUC)). The dots keep running for a while and then the monitor sort of turns itself off and then on again and i get a bit distorted CLI, after I enter the username and password I can work around the CLI, it becomes compleatly normal, but the GUI does not work. When I try switching to GUI i get the same pic I posted above. Any ideas? 

Thanks in advance :)

p.s. I also tried re-installing the graphics drivers with sudo apt-get remove --purge nvidia-current and then sudo apt-get install nvidia-current but it did not help.

p.p.s. I also tried the option to fix broken packages through recovery mode something did update there but no improvements. Also tried to launch in fail-safe graphic mode, it did not work, just prompted me back to the recovery menu after a while.

---

### Post by Bashing-om on 2013-03-29
[INDENT=2]                  Habermas; Hi again....
This "and it was running just fine for a couple of days," might be real indicative of a hard ware failure. At this point look at the logs and maybe get some pointers on what is going on; perhaps differentiate the graphics driver. I suggest to do as follows.
Boot ubuntu up to a text login:
 @ grub menu edit the line containing "quiet splash" -> remove the terms quiet and splash and insert the term "text"; this boots with boot messages displayed and to a text log in terminal (tty1).
Log in here with user name and password.
Set up log viewing thus: Terminal codes:
```
 
cat ~/.xsession-errors > ~/errors-1
cat /var/log/Xorg.0.log > ~/Xlog-1
sudo service lightdm start
cat ~/.xsession-errors > ~/errors-2
cat /var/log/Xorg.0.log > ~/Xlog-2
```
In your home folder are those 4 files; compare for glaring differences (maybe use 2 terminals side-side?[ctl+alt+f2]) between errors-1 and errors-2; also compare Xlog-1 and Xlog-2. [cat ~/errors-1 in one terminal cat ~/errors-2 in the other terminal]
[/INDENT]

To access your GUI desktop use key combo ctl+alt+f7 and to return to the tty1 terminal ; ctl+alt+f1.[INDENT=3]
good places to start looking

[/INDENT]

---

### Post by Habermas on 2013-03-31
Bashing-om thanks for taking your time to look into this, I really appreciate the effort :) Somehow mystically the computer fixed itself again and afterwards I took your advice and checked out the graphics drivers, apparently I had some experimental untested version running so I set up the recommended version and it's been running fine since then, I sure hope it stays that way :) 

Happy Easter holiday by the way :)

---

### Post by Bashing-om on 2013-03-31
Habermas;

That is a Good thing, pleased that you are up and running. Nothing happens -neglecting boot messages- that is not logged somewhere, thus logs become the first line resource. Greatly pleased that you advised on the outcome for all to see.

Please mark this thread as solved as it aids all: 
interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

ain't ubuntu wonderful ! and a reverential Easter to you also !

---

