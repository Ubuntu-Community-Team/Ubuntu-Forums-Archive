---
title: "No Desktop effects"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by MSdefecter on 2008-02-07
Hi
I am a newcomer to Ubuntu and Linux in general so it is very very possible that I have failed to do something that most people do without thinking about so please be patient with me. I have installed Ubuntu 7.10 64 a few times now and every time I have it tells me that desktop effects cannot be enabled. I was told this was because I have an Nvidia graphics card and I would have to install the restricted drivers but every time I try to open it I am told that my hardware does not require any additional drivers, sorry for being so stupid but please help.

---

### Post by Charcoal1981 on 2008-02-07
> ...every time i try to open it...
Open what exactly?? Your Nvidia card does not need any more drivers to work, as the bundled drivers will work fine for most stuff, but if you want the desktop effects you need the restricted driver.

 Go to "System>Administration>Restricted Drivers Manager" to find out if you have the restricted driver. If not then type:
```
sudo apt-get install nvidia-glx-new
```
then
```
sudo nvidia-glx-config enable
```

in a terminal and try the desktop effects again (a reboot may be required).

---

### Post by MSdefecter on 2008-02-08
Hi 
I have still had no luck enabling desktop effects. I used, 

sudo apt-get install nvidia-glx-new 

and then enabled it with,

sudo nvidia-glx-config enable

I then received the message 

Error: your X configuration has been altered. 
This script cannot proceed automatically. If you believe that this 
not correct, you can update the md5sum entry executing the following 
command: 
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum 
otherwise edit manually /etc/X11/xorg.conf to change the Driver section 
from nv to nvidia.

As a fairly backward person I have no idea what this means, but I still have no effects and I still get the message that my hardware does not require any restricted drivers, when I go into the restricted drivers management.

---

