---
title: "nvidia drivers cause black screen, desktop effects"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by nevernamed on 2007-05-28
I was trying to use the built in desktop effects that come with Fiesty, and it asked me to activate the nvidia driver. I said yes, it downloaded the necesary files. It said that I had to run desktop effects again when the new nvidia driver was running. I rebooted. Everything worked fine until the login screen was supposed to come up. The screen went totally black. I still heard the African drums, but I was unable to do anything. control+alt+backspace restarted x and nothing happened. I can boot to the recovery mode... but I really don't know what to do. Does anybody know why this has happened (i heard something about a bug in the nvidia driver in a different thread) and how to correct it? Thanks in advance.

---

### Post by ruipedroca on 2008-02-02
Try this tutorial i made:

How to install Edubuntu in a computer with NVIDIA or ATI (you need internet access)
or
How to solve the black screen when installing Edubuntu 
(forgive my bad english)

This problem (unusual in Linux) is that Nvidia didn't provide the community with the test drivers. They've tried latter to correct this error, but a bit to late.. so, it's not linux, it's nvidia (or so i've read in the internet!


-install edubuntu using the cd-rom as normally
-when the installation finishes, it needs to reboot 
(in my case, during the installation the dhcp wasn't installed, i was using a static address)
-when it reboots, it shows the horizontal bar, but when it completely grows the screen turns black, this happens because the nvidia driver is missing
-when the screen turns black, press CTR + ALT + F1
-log in the terminal using the username and password set during the installation
-type: 
# cd /etc/network
# sudo chmod +w interfaces [this is needed because the interfaces file is originally read only, so we've got to make it writable]
# sudo vi interfaces [this will open the interfaces file, which needs to be configured properly]
-enter the password set during the installation
-press "i" to enter the vi insert mode
-be sure to change the interface file so it looks like this:

[BEGGINING]
# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interfaces(5).



# The loopback network interface

auto lo

iface lo inet loopback



iface eth0 inet static

address 192.168.10.100 [this must be set to the static address you want to use]

netmask 255.255.255.0 [this must be your netmask, usually equal to this one]

gateway 192.168.10.1 [this must be the ip address of your gateway]



auto eth0
[END]

-press ESC to exit the vi insert mode
-press "ZZ" (capitol zz two times, in order to save the changes)

-now type:
# /etc
# sudo vi resolv.conf
-press "i" to enter the vi insert mode
-just write:
domain edubuntu [this must be the domain you used during the installation: it shows in the terminal, in my case, edubuntu@user
nameserver 195.22.0.136 [this must be the dns you use]
-press ESC to exit the vi insert mode
-press "ZZ" (capitol zz two times, in order to save the changes)

-now you can test your internet access by making ping to the ip adress of another machine 

# cd /opt
# sudo dpkg -i envy_0.9.10-0ubuntu2_all.deb [since i've made several atempts, i'm not sure if this step is the one or the other below (just try), it may ask for the installation cd of Edubuntu for some packages]
# sudo apt-get install -f
# sudo dpkg -i envy_0.9.10-0ubuntu2_all.deb [since i've made several atempts, i'm not sure if this step is the one or the other above]
# sudo envy -t [this will start Envy in the text mode]
-now just type your choice ["1" in my case, and press Enter)
-now it will automatically download and install the drivers you need 
-"y" + Enter (happens twice)
-when it reboots, you will be able to see the Edubuntu normal log in: no more black screen! 
Everything should be ok!

Have fun!



credits:
[http://ubuntuforums.org/archive/index.php/t-132808.html](http://ubuntuforums.org/archive/index.php/t-132808.html)
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

