---
title: "GDM Login Screen Good, Gnome Fails after login"
date: 2007-05-05
forum: Desktop Environments
---

### Post by ChaosN on 2007-05-05
I am a first time Ubuntu user and have just installed 7.04 from the alternative CD in a softwareRaid setup. Everything during the installation was successful. 

When I start up Ubuntu and the GDM login screen comes up, everything is displayed fine. I am able to type in my user name and password. That is when the problem starts. Right after I press enter after typing in the password, it looks as if Gnome desktop is going to load, but then it looks like a dialog box of some sort pops up, except it is all distorted and unreadable. Or maybe it's just login box getting distorted as Gnome attempts to load. After that Ubuntu is unresponsive and I just have to restart the computer. I should also mention that the login screen will become unresponsive and a little distorted if I click on the settings button in the bottom left hand corner and select any of the options under there.

I have tried fixing the Xorg configuration files and gone through whole "sudo dpkg-reconfigure xserver-xorg" process a few times. I always end up where I was with the login screen working fine, but the display/ desktop environment seems to crash or freeze after i login (note i have never actually made it to the Gnome desktop environment after logging in). 

The only thing I can think of is the screen settings within Gnome's XML configuration registry are not equal to the /etc/X11/xorg.conf settings. I got that idea from this link: [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-84978c53ee5461d0924f8298527f4fbc891328c9](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-84978c53ee5461d0924f8298527f4fbc891328c9)

Sorry for the length, but trying to give you all the information I can. Thanks in advanced for any help you can provide me!

---

### Post by taurus on 2007-05-05
At the GUI login screen, press <Ctrl><Alt>F2 and see if you can log in with your username and password.  Then, post the output of this command.

```
df -h
```

---

### Post by ChaosN on 2007-05-05
taurus thanks for you quick reply.

While I was waiting for a reply I decide to play around with xserver config some more. This time I changed the video driver to VESA instead of nv. I have a GeForce 7800 so I had originally been using he nv driver. After I completed the config and restarted GDM I tried logging in and it work this time. I am now at the Gnome desktop but and error pop up right away stay "Internal error failed to initalize HAL!" I'm not at all sure what this means.

I restarted my computer and went ahead and ran those commands you gave me anyway. Here is the output: 

Filesystem                   Size     Used     Avail     Use%     Mounted on 
/dev/md0                    19G     2.0G     16G         12%     /
varrun                        1.5G    100K     1.5G        1%      /var/run
varlock                       1.5G          0      1.5G        0%     /var/lock
procbususb                1.5G     144K     1.5G        1%     /proc/bus/usb
udev                          1.5G     144K      1.5G       1%     /dev
devshm                      1.5G         0       1.5G        0%     /dev/shm
lrm                             1.5G       33M     1.5G        3%     /lib/modules/2.6.20-15-generic/volatile
/dev/sda1                 464M      21M     420M       5%     /boot
/dev/md1                    47G     181M      45G        1%     /home

Hmmm it the above lines show up correctly when I typed it in, but it shows up all wrong after I submitted the post. I guess its just squeezed together.

---

