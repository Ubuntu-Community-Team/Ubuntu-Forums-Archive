---
title: "Kubuntu + Nvidia Driver gives me no GUI"
date: 2007-06-19
forum: Desktop Environments
---

### Post by syko21 on 2007-06-19
I recently did a fresh install of Kubuntu 7.04 and kept my home partition from a previous Ubuntu install. Everything transitioned perfectly except when I went to install the nvidia driver. I used the beta driver off their site and it worked fine as long as I didn't restart the computer. However right after I did so the login manager would not load, I would just see a non-moving ui-splash screen for about 20 seconds and it would go to a blinking cursor. Hitting alt+F1 at this point would get me to a TTY terminal. I attempted startx and sudo /etc/init.d/kdm restart but neither worked. Startx gave me an Xorg error saying I had a kernel(?) mismatch for the driver. kdm restart put me back at the ui-splash screen. Anyone have any ideas on how to install the driver so this doesn't happen?

PS> I installed the driver through adept in another install as well with the same results.

Hardware:
HP dv6000t
Intel Core 2 Duo T5600 1.83GHz
2GB Ram
Nvidia GeForce Go 7400
Partition setup
/dev/sda1 = / 10GB
/dev/sda2 = /home 80GB
/dev/sda3 = swap 4GB

---

### Post by syko21 on 2007-06-19
bumpity, please help me =)

---

### Post by angryfirelord on 2007-06-19
First, get into a terminal and remove all traces of nvidia drivers.

Now, execute the following commands:
```
sudo apt-get install nvidia-glx
sudo dpkg-reconfigure xserver-xorg
```
When you're configuring your xserver, select nvidia as your driver from the list. Accept all defaults until you hit the resolutions. Select the ones for your monitor (usually it's 1024x768, 800x600, and 640x480). Next, choose "medium" for the best resolution and select the resolution you want to use. Once it's done, reboot.

---

### Post by syko21 on 2007-06-19
solved.
envy = the absolute best way to install drivers.

---

### Post by angryfirelord on 2007-06-20
You could do it that way, but I prefer doing things the Debian way.

---

### Post by syko21 on 2007-06-20
i prefer it that way too except my kde kept disappearing because of it

---

### Post by stchman on 2007-06-20
> **syko21 said:**
> I recently did a fresh install of Kubuntu 7.04 and kept my home partition from a previous Ubuntu install. Everything transitioned perfectly except when I went to install the nvidia driver. I used the beta driver off their site and it worked fine as long as I didn't restart the computer. However right after I did so the login manager would not load, I would just see a non-moving ui-splash screen for about 20 seconds and it would go to a blinking cursor. Hitting alt+F1 at this point would get me to a TTY terminal. I attempted startx and sudo /etc/init.d/kdm restart but neither worked. Startx gave me an Xorg error saying I had a kernel(?) mismatch for the driver. kdm restart put me back at the ui-splash screen. Anyone have any ideas on how to install the driver so this doesn't happen?

PS> I installed the driver through adept in another install as well with the same results.

Hardware:
HP dv6000t
Intel Core 2 Duo T5600 1.83GHz
2GB Ram
Nvidia GeForce Go 7400
Partition setup
/dev/sda1 = / 10GB
/dev/sda2 = /home 80GB
/dev/sda3 = swap 4GB

Just enable the restricted driver for your card.

---

