---
title: "Gnome hangs on login."
date: 2008-07-15
forum: Desktop Environments
---

### Post by skmassey on 2008-07-15
Hi,

I have a machine at work that hangs when I try to login to gnome.  The first time I login after a fresh reboot, I get into the system and the desktop, a few seconds later the panel stops responding, but I can still click on icons.  When I click on my shell icon on the desktop it opens with a window border, but where the terminal should be, it is white.  Once I ctrl+alt+backspace, it reboots and ends up with a gray box in the top left corner and a light brown background.  Compiz is not on as I am not using the Nvidia driver.  I recently reinstalled, because this problem happened last time.  Last time I was using the Nvidia driver.

The machine specs are:

Intel Pentium D 3.2GHz
4GB RAM
256MB Nvidia GeForce 7300 LE

---

### Post by skmassey on 2008-07-17
I found a few threads that talk about a similar problem.  In this thread
[http://ubuntuforums.org/showthread.php?t=854084](http://ubuntuforums.org/showthread.php?t=854084)

it seems that the gnome-settings-daemon is the culprit.  I have tried killing the process while the problem showed up, and it restarted, but still it just sat there.  My suspicion is, the gray box is probably an error report dialog, but with no window manager running, I can't do anything with it.  Any help or ideas on how to solve my problem would be greatly appreciated.

---

### Post by skmassey on 2008-07-21
I have been updating this machine every time I get a chance hoping that an update will come out to fix it, but I'm afraid there isn't enough information about the error to report for someone to even begin fixing it.  If anyone could help me possibly gather more information to even be able to report a bug, that would be nice.

---

### Post by skmassey on 2008-07-22
I just tried to boot the 8.04 Live CD on a different machine and managed to get a smiliar error.  This time the gray box appeared, but after a minute or two, some text formed in the window and said that the gnome settings daemon couldn't start, but I closed the box and the desktop loaded.  I am currently installing ubuntu on that machine now in hopes that I can narrow down the problem.

---

### Post by ububbatu on 2008-07-25
I have a similar issue.  Once I login, It stays on a brown screen.  I suspect the grey box is a crash dump report.  One complication is that it doesn't happen every time. I've read something about gnome settings daemon being the culprit and have found that a reboot almost always fixes the problem though not always. I'm running compiz and have the problem with or without it. I've had this problem since edgy, off and on, and find that now I can't login to other terminals on the machine when this happens.  I would assume that I could still ssh.  It's hard to locate the offending part of gnome.  If I cat the .xsessions log there is a warning about GTK+ and setuid. There's nothing to refer to this in /var/log/messages or dmesg.  I appears as thought the machine is booted completely and properly - it even plays the jungle music to prove that it has indeed booted properly. I have reinstalled multiple times.  I have not formatted my /home.  I suspect that their is some lingering setting in /home/user that is causing this problem.  I am a little ticked that this seems to be a common problem -multiple bug reports and there seems to be no resolution.  [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/136529](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/136529)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/184879](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/184879)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/158167](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/158167)
there's a set of bug reports and forum post for each way of referring to this problem -gnome hangs- ubuntu locks up- the "Brown Screen of Death".  Each forum or bug post contains post of solutions which -to varying degrees- work for some but there remains that a considerable group that finds no solution.
I have since loaded xfce and enlightenment and both work without fail-so this is isolated to gnome and I believe that it is connected with the user's home directory and that's why creating a new user solves the problem.  Long story short:  Create a new user and move your documents only - no hidden files- and delete the old home directory.  

I wasn't aware that there was another Linux user in MS.  I'm at Bogue Chitto, MS.  SO there are 2 of us.  Good Luck.

---

### Post by lordadi on 2008-07-25
Hi,

When you start up the computer, before login, select sessions > run xclient script. It "might" solve the problem.


Cheers,


Lordadi.

---

### Post by ububbatu on 2008-07-25
@lordadi
Does that fix it for that login or from now on?

---

### Post by globetrotters1 on 2008-07-27
Hi, I have the same problem somehow and I'm really interested to get that problem solved as I have 7 computers to switch from WinXP to Ubuntu.

History:
I installed the first server machine (7.10 Server) which went fine. Then the desktop onto it, worked fine too. When upgrading to 8.04.1 Hardy the machine booted but didn't even fire up Gnome. I could try whatever I wanted, no go...
So I restartet with Ubuntu 8.04.1 Server, installed fine. Added the desktop and ran into the same problem. Gnome wouldn't load. Another no go...
Now I installed Hardy 8.04.1 Desktop which went fine. Then tried to install the LAMP Server onto it, which crashed on me in the MySQL installation script. If I now start the server everything seems to work fine EXCEPT that Gnome setting daemon crashes on me. Brown screen with a displaced login field (looks like it would paint a 1600x1200 resolution screen on a 1280x1024 screen), goes blank for a while, paints a white rectangle in the upper left corner of the screen, waits let's say 2-3 minutes without anything and then fires up Gnome desktop with the message 

"There was an error starting up the Gnome settings daemon"
and
"last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection broke."

Well, as a noob in Ubuntu I tried to find the solution for my problem here and on the net - to no avail.

Do you have any suggestions how to try to solve this? Would be very much appreciated. And if you have a suggestion I would appreciate it very much if you would tell me the Linux commands I have to use in the console window. Learning every day, but it's a getting used to (after so many years of fiddling around with Windoze systems). I definitely like Ubuntu better, just have to get it to run smoothly...

Thanks for reading
Martin
(globetrotters1)

---

### Post by skmassey on 2008-08-05
I reinstalled again, and ended up installing the same exact packages that one of the working machines in my office is using and that seemed to fix the issue.  I still have no idea what package was causing the error but my issue is resolved.  Thanks for the help.

---

### Post by robertjschulz on 2008-08-14
Hi!

This happens if you killed your loopback device

check, if your loopback device is working!

use 
ifconfig
ifup lo
vi /etc/network/inerfaces
perhaps need to add these 2 lines:
auto lo
iface lo inet loopback

I experienced this once during an update and once after playing around with stupid graphical inet configuration

bon chance!

---

