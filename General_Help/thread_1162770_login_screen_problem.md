---
title: "login screen problem"
date: 2009-05-18
forum: General Help
---

### Post by Sashamaru on 2009-05-18
I'm new to ubuntu (installed wubi 9.04 jaunty) and i have this problem.... after i installed tha ati drivers (4850 x2) i was directed to the login screen (the terminal) so i put my name and pass and then it shows only the prompt..... the first time it did that i searched and found that 
 sudo shutdown -h now
worked...... so then i installed again the drivers and the CompizFusion (which when i tried to use it came up with a white screen and there was nothing that i could do so i rebooted every time)... but after the drivers were installed THAT happened... i thought that the shutdown option is going to work but i was wrong... i googled and searched here in the forums about the problem but none of the answers helped me.... i even tried to install new drivers with envy but no luck there (except if i'm making a mistake somewhere that i don't know).... 
if i try 
 sudo apt-get remove xserver-xgl
it says "couldn't find package xserver-xgl"
and in the beggining it also says (after about 10 seconds) *Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon"
i don't know if the 2 things above are of any interest but i thought i should give everything that i see.... 
every suggestion is welcomed :D
sorry for my english.... and for the long speech

---

### Post by Sashamaru on 2009-05-18
am i the only one with this problem??

---

### Post by Legace on 2009-05-18
> **gocek said:**
> 
Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

And this is how to install the drivers properly:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

and do the "manual installation" STEP BY STEP.

---

### Post by Sashamaru on 2009-05-18
well i removed the drivers.... but again i can't get past the prompt login screen... anyway i followed the steps in the manual installation and in the 2nd step i get the error "sh: Can't open ati-driver-installer-9-4-x86.x86_64.run"
what shall i do??  i tried running it as super user but again nothing...

---

### Post by Sashamaru on 2009-05-18
also how am i supposed to download the catalyst if i'm not able to get past the prompt line?? and if i install it how can i change the directory of the installer (which i think that's why the problem before comes in)???

---

### Post by Sashamaru on 2009-05-18
ok for anyone other out there i managed to solve it........
sudo su
cd ~
X -configure
cp xorg.conf.new /etc/X11/xorg.conf
reboot

and then  
 sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
startx

and everything is ok...

---

