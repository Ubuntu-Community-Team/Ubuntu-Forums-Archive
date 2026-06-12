---
title: "Problem logging into to window managers after fresh install - thrown back to gdm"
date: 2006-11-01
forum: Desktop Environments
---

### Post by svamppi on 2006-11-01
So I originally had a 5.04 install that I had upgraded several times (each time accumulating a small error or two). When going from 6.06 to 6.10 however the upgrade-manager crashed halfway through. After waiting for a while, and giving up I rebooted and found out ubuntu wouldn't start anymore. So I DLed the desktop live CD and tried to see what I could accomplish. This was the first time I ran into the problem I have now. After the default ubuntu user had logged into to gnome it only took a few seconds before the screen went black and then I was presented with the gdm again.

Since it was my secondary PC and I didn't have anything extremely important on it, I decided to do a fresh install with the alternate install CD. I have two hard drives, the primary has XP and the secondary has Ubuntu. I reformatted the secondary HD and used the default partitioning suggested in the install. The installation went smoothly. However, when the PC finally rebooted and I tried logging into gnome I had the same problem as when trying out the live CD on the system that had gone bad from the dist-upgrade earlier.

I enter my name and password. Gnome starts loading, it only gets as far as loading the "update notifier" on the progress screen that shows, then it shows me my desktop for a few seconds, then a black screen and then it's back to gdm. If i start messing with the text-mode terminals ctrl+alt+fx i can at least login to my system but switching between text mode and graphical mode more than a few times makes the system lock up completely. So I tried installing xfce4 and using that but it's still the same getting thrown back to gdm after trying to login.

I tried logging in to text mode and running sudo /etc/init.d/gdm stop to stop the gdm then startx to see if I could get some kind of error message, but that didn't work either.

I tried logging in to a failsafe gnome session but that does the same.

This is all very confusing, since the system has been running perfectly fine from 5.04 up until now.

---

### Post by catlett on 2006-11-01
Try reformatting the drive instead of just letting the installer make a partitioning scheme. Use the desktop live cd to run gparted. Delete all the partitions and format the entire drive as fat32. When it is done, select the drive again and choose to reformat to ext3. (this may be overkill. you could probably erase and format ext3 but I always take the safe course)
Then run the installer. What I think happened, is the installer is not overwriting files that are already there. It seems the installer recognises a file it is about to create and leaves the file there. I thinkl you still have a messed up file from your upgrade on your hard drive. That i why I mentioned reformat with a different filesystem. That way the drive will definately be reformatted.
My assumption is that a reformat that definately erases all data will get rid of that file and the installer when run again will create an error free install.
That is just what I would do to start troubleshooting

---

### Post by svamppi on 2006-11-01
Well as I mentioned, I can't get the liveCD working, it has the same problems (gparted is a gnome app right?) . I can however use the alternate install CD and get a shell in the hdb1 partition where I tried to install ubuntu. Can I run some command that will completely wipe the disk from there?

---

### Post by catlett on 2006-11-01
If you get a bash shell, there is a command to make ext3 filesystem out of the drive. First make sure you have a bash shell
```
    #!/bin/bash
```
Then give the command. This command will format the entire drive to ext3 and it assumes you want to format the entire first hard drive.
```
sudo mkfs.ext3 /dev/hda
```
If you can't get a bash shell, get the disk utility from your hard drive maker. They all provide free software that can reformat or diagnose a hard drive. This is just  an example. (Seagate's download site)[http://www.seagate.com/support/disc/utils.html](http://www.seagate.com/support/disc/utils.html)

---

### Post by svamppi on 2006-11-02
Hey again,

So I wasn't able to reformat it to ext3 witk mkfs.ext3 but instead I logged into XP on the primary drive and used the cmpmgmt.msc tool to reformat the entire secondary drive that I've had ubuntu installed on earlier to NTFS. Then I copied it almost full of random files. Then I tried running the live desktop CD again but it still does the same thing. I figured it wouldn't make a difference if I install ubuntu on to this disk, as long as the live CD doesn't even run correctly. Does gnome happen to have any default settings that could cause problems with older hardware these days?

---

### Post by catlett on 2006-11-02
Sorry your having so much trouble. Now that you mentioned it, you may want to try running the kubuntu or xubuntu installation cd.
[http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php)
[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/)
They all have the same base system, it is the desktop that is different. Just in case you want to try, these are the commands to install gnome, kde and xfce. (What I mean is if you get kubuntu or xubuntu installed, you can then open a terminal and install ubuntu/gnome)
After you install any version (K, X, U) buntu you can open a terminal and install the other desktops.
For Ubuntu/gnome desktop```
 sudo aptitude install ubuntu-desktop
```
For Kubuntu/kde desktop ```
sudo aptitude install kubuntu-desktop
```
For Xubuntu/xfce desktop```
 sudo aptitude install xubuntu-desktop
```
Hopefully it is a gnome issue and you can get in this way. Actually you could do the simplest install, the server install and then add gnome later. To install gnome with a server install, run the installer and then reboot. You will be given a text based login. Log in with the user name and password you created. Then you will be at a command line. At that line, enter the desktop command above for ubuntu or kubuntu etc. When you reboot, you will get a gui based login and you will have an install like you would have with the live cd.
I don't know if this is what you meant but it is a different way to get the result you wanted. If this doesn't work, you may want to try a different live cd just to see if another distro can load or not.

---

### Post by svamppi on 2006-11-02
Hmm, well earlier when I had a messed up install I had already installed xfce4 and tried logging into it with the same result. Getting thrown out to gdm. Some X problem?

Earlier tonight I pulled out my old CD and installed 5.10 again. Works perfectly, like before. It's just a shame that I had to go 1 year back in time with the new version... :(

---

### Post by msmarcal on 2006-11-03
I'm having the same issue here.

I've tried to install ubuntu 6.10 (regular and alternate install), xubuntu 6.10 (regular and alternate install) and I got the same issue.

---

### Post by svamppi on 2006-11-03
Maybe we could try comparing some hardware specs and see if we can find some pattern. Mine is a pretty old P3 600MHz with 384 MB RAM and a voodoo 3 3500 TV card. When I tried googling for the problem at first, somebody else had a similar problem and said it was related to panel transparency in gnome. But I guess that would be turned off by default so maybe it doesn't have anything to do with us?

---

### Post by msmarcal on 2006-11-03
Mine is a P3 450 Mhz with 256 MB RAM and a Voodoo 3 2000 video card.

I've found this bug report: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-tdfx/+bug/63796/+viewstatus](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-tdfx/+bug/63796/+viewstatus)

I think it is the same we are experiencing.

---

### Post by msmarcal on 2006-11-03
Update: If you just switch to "vesa" driver it'll work but without any acceleration.

---

### Post by svamppi on 2006-11-04
Ah ok, how do I do that then?

---

