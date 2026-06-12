---
title: "Usb problems in 10.04"
date: 2011-11-02
forum: Desktop Environments
---

### Post by wallytheaviator on 2011-11-02
Hey everyone,

I have tried to figure this one out for the last few hours.  

I built a custom pc for a friend using 

300W Power supply
Gigabyte mini atx motherboard
2 4gb gskill ram ddr3
Amd phenom II x4 2.8
Dvdrw drive, card reader, 500gb hd


The problem is that the keyboard and mouse will at random freeze up and not respond or send false signals from the keyboard. Here is the interesting part.   She has a new dynex keyboar and mouse combo.  The one i used to configure bios and to install and test the system was an older model dynex keyboard and a microsoft mouse.  It ran great for 5 hours with not a single problem.  

I ran an update and also brought over my old dynex keyboard but now it is doing the same thing.  

Could this be bad usb ports on the motherboard? Or will i need to do a reinstall of the os? I highly doubt both keyboard and mouse could be defective, and i think the power supply is big enough to handle everything.  


Sorry to trouble you all with this.

I did however have a ps2 keyboar which i pligged in to test for a few minutes and it worked.   Could that have caused it to expect a ps2 setup for the main input?

How would i be able to trouble shoot this problem? 

Also its the 64bit os.  

Thanks
Walter

---

### Post by typhoon_tip on 2011-11-02
Try to start the system again from the liveCD (try Ubuntu, same version, same bitssssss), with the bad keyboard/mouse connected, and see if you get the same troubles or not. If yes, it is very likely BIOS/HW issue.

---

### Post by wallytheaviator on 2011-11-02
Update

I ran the ubuntu 10.04 installation cd and still it froze up.  

I then tried ubuntu 11.10 and installed the upgrade for it.  It ran for about 8 hours before the mouse froze up again.  

I tried another mouse and still had the same result.  Bios checked out.  So i am assuming a semi defective motherboard.  Is that even possible for it to boot properly but have intermittent usb ports?

Also the data transfer rate is very slow compared to another system running sata3 hd and dvdrw drive.  

Thanks for the help

---

### Post by wallytheaviator on 2011-11-04
> **typhoon_tip said:**
> Try to start the system again from the liveCD (try Ubuntu, same version, same bitssssss), with the bad keyboard/mouse connected, and see if you get the same troubles or not. If yes, it is very likely BIOS/HW issue.

Just thought of this

Is it possible to have an error with it being an nvidia chipset?

I know ati has never given me problems.  I dont know how nvidia does for everyone else.

---

### Post by wallytheaviator on 2011-11-06
Update...
 
So swapping the usb mouse with another ( wireless) still did not fix the problem, it is not the motherboard, it is not the mouse, and its a fresh install again, its updated. 
 
I dont know much else about what it could be that is causing the problem.
 
Anyone have any ideas?

---

### Post by pavi_elex on 2011-11-08
```
root@user-desktop:~# sudo nano /etc/X11/xorg.conf
```& add following code into file & save it.

```
Section "ServerFlags"
Option "AutoAddDevices" "false"
EndSection
```or

```
sudo apt-get install xserver-xorg
```

---

