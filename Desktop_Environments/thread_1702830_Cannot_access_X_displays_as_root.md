---
title: "Cannot access X displays as root"
date: 2011-03-08
forum: Desktop Environments
---

### Post by ejee on 2011-03-08
Hello,

I have made a script to dump screenshots on Ubuntu regularly, as a way to keep track of what happens on the machine ("Big Brother is watching you" sort of system :))

The script is run through inet.d as root, and used to work happily under Ubuntu 10.04. However, since the upgrade to 10.10 it broke. So what is the problem?

Here are the lines that give trouble (simplified version):

time=$(date +%d-%m-%Y_%H-%M-%S)
/usr/bin/X11/xwd -display :0 -root > /home/ej/$time.0.xwd 
/usr/bin/X11/xwd -display :1 -root > /home/ej/$time.1.xwd 

This now gives the error:
/usr/bin/X11/xwd:  unable to open display ':0'
/usr/bin/X11/xwd:  unable to open display ':1'

It simply means root has no access to these displays!

If I run this script as a normal user, I will get a dump file for the display of that user. Also, if I use xauth to merge the xauthority file of both users at :0 and :1, I can dump both displays at once (until I reboot and the authority files are readjusted...). But this is not what I want; I want root at bootup to be able to access my X displays!

What happened in the security that I am (no longer) able to do this? Many thanks in advance!

---

