---
title: "Error With Asus Geforce 6800gt"
date: 2006-01-08
forum: Desktop Environments
---

### Post by sjlanda on 2006-01-08
1.st boot after installation with ubuntu 5.10 works well with my geforce 6800gt pci-e card. I get all the way into X. But 2.nd boot is a failure! I get a blue screen and an error message that says something about x window error and/or graphic error. Then, X wont start. Instead i must logon from the text-based logon. Somebody help me please:) 

It's weird, since my last graphic card ASUS GEFORCE 6600GT worked without any problems:confused:

---

### Post by Ampersand on 2006-01-08
Select 'Yes' from the message that appears asking if you want to see the output, and post the lines starting (EE) here. Generally, running 
```
sudo dpkg-reconfigure xserver-xorg
```
helps.

Are you using the nvidia drivers (did you install linux-restricted-modules, nvidia-glx)?

---

### Post by zappa86 on 2006-01-08
I have the exact same card and I had a similar problem. Did you install the nvidia drivers from their website, or from synaptic, or not at all? Also if you would be so kind as to put your Xorg.conf up here we could better help you.

---

### Post by sjlanda on 2006-01-08
hi thanks for helpin'

I have done sudo dpkg... and it helped some. I got into the graphical X, but there is still only 640x480 pixels and no way to change it. It is also some flimmering (19" lcd) that shouldnt be there. I dont know if i did all the "reconfigure" as it should be but at least i tried. It sucessfully detected the video card and the monitor. Anyways, here is what the error message was about:

(EE) Unable to find a valid framebuffer device
(EE) NN(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
(you may have to look at the server log to see the warnings)
(EE) Screen(s) found, but none have a usable configuration,

Fatal Server Error
No Screens Found


Does (part of) the problem occur because i downloaded the 2.6.10 or doesn't the geforce 6800gt work with linux or what?:???:
I did not install any driver at all. I thought ubuntu would detect it automatically as it did with asus geforce 6600gt.

---

### Post by zappa86 on 2006-01-08
I'm just wondering how you got your nvidia drivers? was it from their website or from synaptic. Also if you could copy and paste your Xorg.conf into this forum it would be helpful. the file is located at:
/etc/X11/xorg.conf and if you open up the console you can type:
```
gedit /etc/X11/xorg.conf
``` and copy and past it here.
also do a:
```
lsmod | grep nvidia
```
and tell us what you see when that happens. (if anything).

---

