---
title: "Cannot wake up from sleep/suspend on xubuntu 13.04 - solved"
date: 2013-05-08
forum: Desktop Environments
---

### Post by rom515 on 2013-05-08
Hey Everyone,

I have been reading many posts on how to fix this issue in xubuntu 13.04, but only one worked for me and I had to do it in the order below. Now I can enjoy the latest xubuntu. :)

* How to fix xubuntu 13.04 from not waking up from sleep / suspend
* How to get NVIDIA drivers working and replace Nouveau Default Drivers in Xubuntu 13.04
* Do not remove the nouveau drivers (I left them alone)

1) Using Synaptic Package Manager install "gedit", if not already done, or at the terminal type:
 sudo apt-get install gedit

2) At the terminal type:
 sudo gedit /etc/default/grub

3) Add "nouveau.blacklist=1" to "GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash"
 (Ex.) GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 quiet splash"

4) Save the grub file

5) At the terminal type:
 sudo update-grub

6) Reboot

7) Using Synaptic Package Manager install "nvidia-current", which will pull down a number of other dependencies, or using the command line type:
 sudo apt-get install nvidia-current

8) At the terminal type:
 sudo nvidia-xconfig

9) Reboot

10) Check to see if NVIDIA is working correctly by going to "Menu >> Settings Manager" and under "System" open "NVIDIA X Server Settings". There should be no errors listed on the main screen, "X Server Information".

11) Test your computer when in sleep/suspend mode and see if it starts normally.

12) Enjoy!

---

### Post by Toz on 2013-05-08
Welcome to the forums and thanks for sharing.

Just one comment, though. You don't need to install gedit in xubuntu 13.04 - it comes with mousepad which could be used instead (versions lower than 13.04 have leafpad installed). So:

1) no need to install anything

2) At the terminal type:
sudo mousepad /etc/default/grub

Note: Installing gedit will also bring in some unnecessary dependencies.

---

### Post by rom515 on 2013-05-08
Thank you for that comment. I am so used to using Gnome I forgot. This is my first time using XFCE and I love it so far.

---

### Post by kakaomannen on 2013-07-13
rom515,

Thanks a lot for this, I have been messing around in both Mint 15 and Ubuntu 13.04 with the same problem for 2 weeks now, and your solution worked!:D I knew the problem was in the GRUB file I just couldn't figure out what to type

---

### Post by vikram_kapoor on 2013-08-22
Good helped me alot.

---

