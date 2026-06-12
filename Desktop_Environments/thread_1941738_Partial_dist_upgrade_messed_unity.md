---
title: "Partial dist upgrade messed unity"
date: 2012-03-16
forum: Desktop Environments
---

### Post by pmatos on 2012-03-16
Hi,

I have been on 11.10 since release and today I got notification of a partial dist release. After that it recommended me to restart and I did so. Upon starting Unity, it just shows the background and a themeless bar on top and nothing else. I need to kill Xorg and start with Ubuntu2d to have any luck into using ubuntu.

Any ideas what the problem might be or where unity writes its logs so I can understand what's going wrong?

Cheers,

Paulo Matos

---

### Post by jerrrys on 2012-03-16
it can happen

[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by pmatos on 2012-03-16
> **jerrrys said:**
> it can happen

[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

Oh great! Should've seen that before. I guess in time I will get another partial upgrade that will fix things?

---

### Post by jerrrys on 2012-03-16
That is (should be) correct

You can always try in terminal:

sudo apt-get update

---

### Post by pmatos on 2012-03-19
> **jerrrys said:**
> That is (should be) correct

You can always try in terminal:

sudo apt-get update

Unfornately no update shows up since I messed up the system. Now, whenever I open a terminal, nothing shows up, logging in takes ages, etc etc.

Any suggestions on how to force reinstall of all the basic ubuntu desktop packages?

Cheers,

Paulo Matos

---

### Post by jerrrys on 2012-03-19
Try this to get a terminal.

Load ubuntu and press **Ctrl Alt F5** keys at the same time and then try to log in.

If you get that far then enter:

sudo apt-get update

sudo apt-get upgrade

sudo reboot

---

### Post by pmatos on 2012-03-19
> **jerrrys said:**
> Try this to get a terminal.

Load ubuntu and press **Ctrl Alt F5** keys at the same time and then try to log in.

If you get that far then enter:

sudo apt-get update

sudo apt-get upgrade

sudo reboot

Here's what happens, if I go to a virtual terminal, F2 for example, I login and it takes ages. If I do Ctrl-C, I get a prompt. Doing apt-get update/upgrade shows nothing.

I can get into X but login takes ages. Then everything seems to be fine until I try to open a terminal (gnome-terminal/Xterm you name it), it takes forever to load it and I end up giving up.

---

### Post by jerrrys on 2012-03-19
what about rescue mode

---

### Post by pmatos on 2012-03-20
> **jerrrys said:**
> what about rescue mode

Rescue mode worked but normal mode didn't. Went nuts and did a dist-upgrade to 12.04.

Unfortunately not all is well, even though a lot of things got better.
I can only start Ubuntu 2D. Normal ubuntu login fails because unity bar and top bar don't load. Any way to understand what's going on (log file)?

---

### Post by jerrrys on 2012-03-20
Wow, upgraded to 12o4, I'm impressed.  But thats probably the last thing you wanted to do.  Im running 12o4 and its good, but still a work in progress.  I think you have added to your problems.

---

### Post by pmatos on 2012-03-20
> **jerrrys said:**
> Wow, upgraded to 12o4, I'm impressed.  But thats probably the last thing you wanted to do.  Im running 12o4 and its good, but still a work in progress.  I think you have added to your problems.

Well, it was a drastic action but at least now I can work. Before I couldn't so all in all it was a positive decision.

I just can't login into Ubuntu - normal mode. Any ideas where the logs are (if unity dumps logs...)?

---

### Post by jerrrys on 2012-03-20
> **pmatos said:**
> Well, it was a drastic action but at least now I can work. Before I couldn't so all in all it was a positive decision.

I just can't login into Ubuntu - normal mode. Any ideas where the logs are (if unity dumps logs...)?

Your /var/log files can be view using the "System Log Viewer"

[ATTACH]214656[/ATTACH]

Two other commands to try that will attempt to fix broken packages:

sudo dpkg --configure -a

sudo apt-get install -f

---

### Post by pmatos on 2012-03-27
> **jerrrys said:**
> Your /var/log files can be view using the "System Log Viewer"

[ATTACH]214656[/ATTACH]

Two other commands to try that will attempt to fix broken packages:

sudo dpkg --configure -a

sudo apt-get install -f

Thanks, a couple of installs and upgrades later and everything seems to be fine.

---

