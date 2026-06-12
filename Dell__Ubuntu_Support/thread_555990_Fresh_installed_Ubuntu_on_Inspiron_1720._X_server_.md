---
title: "Fresh installed Ubuntu on Inspiron 1720. X server problems"
date: 2007-09-20
forum: Dell  Ubuntu Support
---

### Post by DMS321 on 2007-09-20
I just installed Ubuntu on my brand new computer, and I get the following problem when booting.

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

I select yes, and of course it's all in gibberish that I don't understand one bit of. It never gives me an option to reconfigure X, either. Then it just goes to a terminal and every 30 seconds spews out a:

"bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed"

I have no idea what this means, and it seems that I can't do anything more after this. I tried logging in under the terminal, and manually reconfiguring X that way, but it didn't help.

Note: I get the Ubuntu splash screen when I boot up, and it fully loads. I get this error after that.

EDIT: Specs are:
Intel Core 2 Duo 2.0GHz
2GB DDR2 RAM
nVidia GeForce 8600M GT 256MB
160GB SATA HDD

---

### Post by ahai on 2007-09-23
I had the same problem and solve it by installing text based ubuntu from ubuntu alternative CD. You have to have internet access. when installation finished I logged in and run following commands:
% apt-get update -y
% apt-get install -y linux-headers- build-essential gcc gcc-3.4 xorg 
Of course, I keep vista and I already downloaded a program called "envy" which is a script to simplify installation of graphic drivers for ATI and NVIDIA. Second I copied envy from vista partition to my home catalog:
% cp /media/sda1/dell/envy-xx /home/abbas
you have start envy in text mode:
% sudo tar zxvf envy-xx
%sudo envy -t
choose alternative 1 to install NVIDIA driver and follow instructions and let envy write configuration to your X server. Then I downloaded gnome:
% sudo apt-get install -y gnome
when it finished I start the X server:
% sudo gdm
And that's it! just log in to your fresh installation of ubuntu.
remember to activate your wireless under menu System->Network in my case eth1.
Good luck

---

