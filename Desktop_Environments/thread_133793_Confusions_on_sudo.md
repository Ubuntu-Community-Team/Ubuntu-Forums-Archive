---
title: "Confusions on sudo"
date: 2006-02-20
forum: Desktop Environments
---

### Post by deltan.cc on 2006-02-20
Hi there,

I'm a new ubuntu user. I spent quite some time wrestling with getting my Xserver (I think this is the correct term) to work with my ATI X200 graphics cards. There were many helpful forums pointing out that at least as a stop gap measure, I should switch the driver from 'ati' to 'vesa'. It worked, but it didn't work the way the posts said it should and I'd like to understand why.

All the commands I saw asked me to log in to a terminal prompt, then type "sudo" and a series of commands, either to edit the config file or to run through the configuration process again (dpkg-reconfigure .....). 

My understanding is that using "sudo" at the beginning of the command means I don't need to log in as a "root user" (another term I'm trying to come to grips with). In anycase, when I logged in as a user, I could type a command (eg. sudo nano /etc/X11/xconfig.xorg or similar) and it would ask me for my password, then do nothing. After hours of rebooting and checking that I had correct syntax and reading other posts, I final decided to try logging in as root. Suddenly, the reconfigure program launched and I could change the driver with ease. So it works, but I don't understand why "sudo" didn't? I did some research on what "sudo" is supposed to do, but that hasn't clarified things much for me. Can anyone provide a short answer that would?

Further to that, I'm trying to master the art of installing applications. Again, I've discovered many fine posts telling me how to install applications using "synaptics". I've also noticed an "add applications" menu option. At least one asked me for my password when I clicked on it, which I duly typed. The window disappeared, but I was not able to install anything. Moreover, following than, I could not even get the window to pop up to enter the password -- just a dull beep type sound that acknowledged I had selected the menu item. I  assume I have missed something here. 

For reference, I am using Breezy Badger 5.10, Dell desktop with an Intel 64-bit processor, ATI X200 card. The software I was trying install was the upgrade to the version of Firefox that came bundled on the Live DVD. 

Any clarification appreciated. And BTW - if I've just missed some posts that will clarify all this, please just point me to them. I'm not afraid of a little reading and wouldn't want to waste time having a well-written answer written out again just for me.

---

### Post by RAOF on 2006-02-20
It sounds like you have installed using the "expert" option.  Is this true?  You shouldn't be able to log in as root under a standard Ubuntu install.

You should be able to fix things by running visudo from a root terminal.  Try the solution in this thread:
[http://www.ubuntuforums.org/showthread.php?t=129857&highlight=sudo+admin+visudo](http://www.ubuntuforums.org/showthread.php?t=129857&highlight=sudo+admin+visudo)

---

### Post by shams2 on 2006-02-20
sudo means to change to root from your user account, in ubuntu you canno't login as root but from your user account you can change to root, to change to root in the terminal type:
sudo su
type your user passworred now you are root, to work in synaptic you must be root in a terminal as root type synaptic,

---

