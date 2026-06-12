---
title: "Crazy X problems"
date: 2008-12-20
forum: General Help
---

### Post by nerfdooker on 2008-12-20
All right so i am just randomly having a huge problem with X.
When i went to login today, i was greeted with a little window telling me "Cannot launch graphical configuration tool because displayconfig-gtk is a not installed" well alright, i dont know why i would need to randomly reconfigure my x but okay..
So i run sudo dpkg-reconfigure xserver-xorg and reconfigure my keyboard options via commandline. After im done i run startx and now i get my desktop. But it seems that my nvidia drivers are disabled, so i go to hardware drivers and get"Failed to run /usr/bin/hwtest-gtk as root= unable to copy users xauthorisation file. Ummm okay, it seems to be doing this every time i try to open something that requires root privileges graphically (sudo from command line still works). Next open the nvidia settings app and get "you do not appear to be using nvida x driver(ect.)
Okay then i allready knew that.. So to enable my driver i run "sudo nvidia-xconifg) and get "Data incomplete in xorg.conf(ect.)"
So i go to ect/x11 and notice that my xorg.conf is rather bare. All it has is 2 input devices (mouse and keyboard) a monitor and device. I saw that i have lots of backup xorg.confs and found a proper looking one with everything in it, delete the xorg.conf and rename the back up to xorg.conf. I reboot, figuring that ive fixed it but once again i am greeted with "Cannot launch graphical configuration tool because displayconfig-gtk is  not installed" :confused: so i have to repeat configuring it from the command line and starting x, then logging on without nvidia drivers. 

Obviously this is bad and i have run out of ideas as to how i fix it. Does anybody know what is going on here?

(ps, my video card is a 8800gt)
(sorry for the wall of text :KS )

---

### Post by Woody1987 on 2008-12-20
Have you tried starting up in rescue mode and selecting xfix from the menu?

---

### Post by Wisp558 on 2008-12-20
sudo apt-get install displayconfig-gtk

I don't konw if it'll work, but hey, why not?

---

### Post by joycerico85 on 2009-01-29
Hello everyone

I am new with Ubuntu, so I will need some guidance.
First of all...a friend of mine installed ubuntu 8.04 in my computer and everything was Ok...until I decided to install compiz...and for some reason...I disable nvidia....before everything look prettier and the nvidia logo showed every time i started ubuntu.
Now....I have this..I dont have the logo anymore and ..everything looks different...I tried to install the driver myself so I Installed
nvidia-config and 2 other more files that it required me...but I still not have installed my nvidia correctly...cause when I go to nvida x server settings it says that I am not using the nvida x driver...
when i typed this...

sudo nvidia-xconfig and I got...

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

but....Im still not using my x driver?? any help will be appreciated!!

Thanks in advance

---

