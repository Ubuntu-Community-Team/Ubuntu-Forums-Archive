---
title: "Black command prompt screen?"
date: 2005-12-22
forum: Desktop Environments
---

### Post by phantomcow2 on 2005-12-22
Im really lost.
I saw all these screenshots of Ubuntu being an interface and all.
But after completing installation, all I see is a black screen. 
It says enter login, enter password. I do
Now it just prompts for a command, i have no idea what to do. Can somebody help? I just want to get this computer to a normal system so i can use firefox and all this. THis is my first time using anything linux

---

### Post by xmastree on 2005-12-22
Try typing **startx** at the prompt. That ought to start the desktop, but with a normal installation that should be automatic, so something is not right.

Run it anyway, let's see what happens.

---

### Post by phantomcow2 on 2005-12-22
Thanks for a quick reply...
I entered startx and it says XUATH creating new authority file (gives a directory).
Then
X: User not authorized to run server file, aborted..


Server file|?

---

### Post by xmastree on 2005-12-22
Damn, I jumped in on this coz it looked like an easy one... :rolleyes:

You shouldn't have to do this, but try **sudo startx** instead. That will run it as root.

Failing that, try ```
sudo dpkg-reconfigure xserver-xorg
```

As for server, the X window system is a server/client thing, but you usually don't see it as that since they're both on the same machine.

Did everything seem to be ok during the install? You should have a graphical login, not a text screen.

---

### Post by phantomcow2 on 2005-12-23
When i started up Ubuntu for the first time, i got a message saying i may have to manually install something because during normal installation something 'may' have not gone right.
I guess thats correct...I will reinstall today

---

### Post by xmastree on 2005-12-23
What's the spec of your system? In particular, the video card.

---

### Post by Ninjagecko on 2005-12-26
When I recently installed Ubuntu, I too only got a command prompt.

This was kind of odd, since it didn't happen the last time I installed Ubuntu... Both times I did a net install and Ubuntu wasn't able to properly download from the files from the us.archive.ubuntu.com. It does not sound like you're doing a net install, but regardless I too got the message that some packages could not be obtained/installed.

My solution:
Manually download the packages myself. (Keep in mind you shouldn't have to do this with a CD install, but it may work anyway. This isn't a viable option unless you have a high-speed internet connection.)

Step 1 -- make sure internet is working
To make sure internet is working, do 'ifconfig' or ping some website you know (e.g. 'ping google.com' and seeing if you get responses back -- if it stalls your connection isn't properly configured; hit ctrl-C and proceed to fix). If your internet is down, you can probably find a guide online or in these forums of how to get it working from the command line. (In a nutshell, first you do 'sudo ifdown eth0' then 'sudo ifup eth0' -- assuming you're using an ethernet connection, as opposed to say a wireless connection which is slightly tricker to get running from the command line. You may have to edit 'sudo nano /etc/network/interfaces'.)

Step 2 -- configure apt-get & install main Ubuntu packages
Then, once my connection was working, I configured apt-get by doing 'sudo apt-get update' and then downloading & installing two packages: 'sudo apt-get ubuntu-standard' and 'sudo apt-get ubuntu-desktop'; these two packages contain the bulk of Ubuntu, and were not installed on my system due to the crummy installer. I then rebooted by doing 'sudo reboot'.

(Terminology: sudo - Supreme User DO - do something as root; apt-get - install and download official packages from online repositories)

---

