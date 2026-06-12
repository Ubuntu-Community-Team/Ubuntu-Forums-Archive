---
title: "Cinnamon Crashes On Login"
date: 2013-10-11
forum: Desktop Environments
---

### Post by Shadius on 2013-10-11
Hey everybody,

I installed Cinnamon with the method [here]("http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html"), using the stable PPA. However, after completing the installation and then updating, I tried logging into Cinnamon and it just keeps crashing. It tells me that it's running in fallback mode and needs to restart Cinnamon. I've tried uninstalling the PPA and reinstalling it and I still get the same thing. Can anyone provide any solutions? Thanks in advance.

---

### Post by AussiePozzie on 2013-10-11
Same problem here. 

It seems that it is related to the cinnamon 2.0 release, as the previous version 1.8 was working fine.

I just finished the weekly update, and out of habit, restarted the machine. I could log on, but as soon as the desktop was coming up, the message appeared, cinnamon just crashed, reverting to gnome. I have since tried to purge it, and install after that, but that made no difference. After some googling, I found that possibly it is related to the nvidia driver, after reinstalling it, there was not difference either.

Any useful suggestion would be very appreciated.

---

### Post by johnston_evo3 on 2013-10-11
Just to add, I came on here because mines doing the same thing.  Been running Cinnamon on 13.04 pretty seamlessly for a while now.  For some reason I restarted after an update this morning (I usually keep this box on 24/7)  and ever since I've been on Fallback mode. 

By the way I'm on an Intel driver.

---

### Post by AussiePozzie on 2013-10-11
After doing some more googling, a accidentally blundering into LinuxG.net, found this article:

[http://linuxg.net/how-to-install-cinnamon-2-0-on-ubuntu-13-10-13-04-12-10-12-04-linux-mint-15-14-13/](http://linuxg.net/how-to-install-cinnamon-2-0-on-ubuntu-13-10-13-04-12-10-12-04-linux-mint-15-14-13/)

It seems that the ppa has changed.

Due to a lot more of 'manouvering', I have managed to kind of reduce my machine to not working, ... I know, I know, and had to rebuild the system from scratch.

In the new installation, I have changed the ppa and installed cinnamon, ...this time around working fine.

Not sure though, if changing the ppa to the abve and doing the distribution upgrade will help you gents.

I hope it does.

---

### Post by johnston_evo3 on 2013-10-11
Aussie that one worked for me.

Big thumbs up :cool:

---

### Post by AussiePozzie on 2013-10-11
Glad to hear it, mate!

However, ...it's not all smooth sailing yet!

There does seem to be a connection between cinnamon 2.0 and nvidia.

After having rebuilt my system and installed cinnamon as per the listed article above, I have tried to update the nvidia drivers too, from the version 304 to versioin 319.

The driver was downloaded alright, but has failed to install.

After rebooting the machine, it hung before reching the login screen. At first I thought it must have been some problem with installation, ...so I reinstalled the sytem once again, tried to update the nvidia driver to 319, and lo and behold, the system hung again after rebooting.

I would suggest, albeit I cannot confirm one way or another that it will work, to:

1. revert to nvidia version 304 (fingers crossed it works)
2. change the ppa according to the above article
3. distribution upgrade cinnamon

Give it a go, ...hopefully not three times over like me!

---

### Post by asavah on 2013-10-11
There is a problem with stable ppa for cinnamon, cinnamon-common package for cinnamon 2.0 is missing in stable ppa.
The easiest way to fix it is to switch to cinnamon-nightly ppa and reinstall cinnamon.
I did this few hours ago and the system is working perfect - fast, smooth and stable.
BTW I use nvidia 325.15 from xorg-edgers ppa.

---

### Post by Shadius on 2013-10-13
Thanks guys. Reinstalling Cinnamon using the nightly ppa worked.

---

