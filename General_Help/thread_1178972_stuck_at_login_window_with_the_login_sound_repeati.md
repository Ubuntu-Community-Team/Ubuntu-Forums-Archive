---
title: "stuck at login window with the login sound repeating...help!"
date: 2009-06-05
forum: General Help
---

### Post by patrick907 on 2009-06-05
Im using jaunty, and upon starting up my laptop this evening ubuntu gets like stuck at the login window (i think), it goes through grub just fine, then the normal ubuntu loading screen, then when the login window should appear the mouse changes to the circle, the login sound plays, and a text box shows up, but not the whole login screen, this stays up for about a second then the screen goes black and it repeats the sound and showing the text box, and so far it keeps repeating this indefinitely 

I looked around on the forums for something like this and only found one post, and the guy there just reinstalled his OS.....i'm hoping that isnt the only way out of this....

in the previously mentioned post they recomend that i try to stop gdm, this worked to stop the sound from playing at least (i was able to get into a shell with ctrl+alt+f1) they also recomended i look at the log for gdm 

in my /var/log/gdm/:0.log the only error i see is:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found) error setting MTRR (base = 0xe0000000, size = 0xff00000, type = 1) Invalid argument (22)

i tried googling that to see if i could find something....but so far i havnt had any luck

if anyone knows what i should try now or if you need more info please let me know...if it is at all possible i really want to avoid having to reinstall ubuntu


thanks

---

### Post by nikhilk on 2009-06-05
To atleast get to a GUI try running the following command on the shell (alt+ctrl+F1)
```
sudo dpkg-reconfigure xserver-xorg
```

You will be asked some questions here, if you do not know answer to any one you can choose the default selection.
When asked about your video drivers, select “vesa” which should take you to your desktop on reboot.

You can then see what the problem is (you probably need to install the correct NVIDIA video drivers).

---

### Post by patrick907 on 2009-06-05
> **nikhilk said:**
> To atleast get to a GUI try running the following command on the shell (alt+ctrl+F1)
```
sudo dpkg-reconfigure xserver-xorg
```You will be asked some questions here, if you do not know answer to any one you can choose the default selection.
When asked about your video drivers, select “vesa” which should take you to your desktop on reboot.

You can then see what the problem is (you probably need to install the correct NVIDIA video drivers).

k, ran that command....answered all the questions....and nothing seemed to happen, it just went back to the command prompt, i tried rebooting, but it is still doing the same thing getting stuck on the login screen

any other ideas?

---

### Post by nikhilk on 2009-06-05
First take backup of your "/etc/X11/xorg.conf" file. e.g.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then check your "/etc/X11/xorg.conf" file for references to either "nv" or "nvidia".
```
sudo nano /etc/X11/xorg.conf
```
Find the "Screen" section and replace the "nv" or "nvidia" line, if any, with "vesa". Then see if a reboot gets the problem corrected.

---

### Post by patrick907 on 2009-06-05
in my xorg.conf file there is no mention of nv or nvidia, my screen section is:

Section "Screen"
           Identifier      "Default Screen"
           Monitor        "Configured Monitor"
           Device         "Configured Video Device"
EndSection

---

### Post by nikhilk on 2009-06-05
> **patrick907 said:**
> in my xorg.conf file there is no mention of nv or nvidia, my screen section is:

Section "Screen"
           Identifier      "Default Screen"
           Monitor        "Configured Monitor"
           Device         "Configured Video Device"
EndSection

Ok, could you just post the contents of your entire xorg.conf file?

---

### Post by patrick907 on 2009-06-05
The formatting is off for this since im just typing it out on my desktop to post it and i didnt copy all the comments at the top but the rest of the info is there

#bunch of comments up here

Section "Device"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
EndSection

Section "Monitor"f
Identifier "Configured Monitor"
EndSection

Section "Screen"
           Identifier      "Default Screen"
           Monitor        "Configured Monitor"
           Device         "Configured Video Device"
EndSection

---

### Post by nikhilk on 2009-06-05
> **patrick907 said:**
> 
Section "Device"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
EndSection


That section seems strange. I am not at my Kubuntu desktop right now so can't confirm but I think there should be a Driver line in the "Device" section. Make sure you have a backup copy of the "xorg.conf" file and add the following line in the "Device" section
```
Driver "vesa"
```

---

