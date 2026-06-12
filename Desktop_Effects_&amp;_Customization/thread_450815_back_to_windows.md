---
title: "back to windows???"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by newboy12 on 2007-05-21
I'm currently running Ubuntu 7.04 at 1024 X 768 with a 17" Dell FP, I have a GeForce4 MX 240 and it is capable of getting much better resolution than this in xp. 

Is there are simple way (being new to linux) that I can increase the resolution as I don't wish to return to the dark side?

---

### Post by jimbean on 2007-05-21
did you go into system- administration and select the restricted drivers manager

---

### Post by lopagof on 2007-05-21
easyubuntu will be worth a shot

---

### Post by newboy12 on 2007-05-21
Yeah, made no difference, just display the resolutions that it did before

---

### Post by SeanHodges on 2007-05-21
System -> Preferences -> Screen Resolution should give you the resolutions available for your monitor as detected by the driver. However, my guess is that you have already tried this...

Often, the reason higher resolutions are not available is that the card has not been detected properly, or that safe ones have been chosen because it has not been tested enough. When this happens, you can configure the server manually by typing the following into a terminal:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-WORKING
```
(to back-up your current settings, then...)

```
sudo dpkg-reconfigure xserver-xorg
```

It will allow you to pick your card type, screen resolution range, etc. 


**IMPORTANT!** You are using an NVidia card, but i'm not sure if you have the restricted "nvidia" driver installed (see above post). To be safe, when the command above asks you for the card type, DONT PICK "nvidia"! Pick "nv" instead, which is definitely available on your system. After you have got this all working, you can set up the restricted driver afterwards if you decide to.

Once you have finished you will need to restart the computer for the changes to take effect (or alternatively restart the X-server by logging out and pressing Ctrl-Alt-Backspace)

You should find your chosen screen resolutions are now available in the 
System -> Preferences -> Screen Resolution utility after this.

Also, if you end up stuck at the terminal because your graphical display wont start, you can revert to your current setup by typing:

```
sudo cp /etc/X11/xorg.conf-WORKING /etc/X11/xorg.conf
```

and rebooting by typing "sudo reboot"

Good luck!

---

### Post by joramdam on 2007-05-21
> **SeanHodges said:**
> System -> Preferences -> Screen Resolution should give you the resolutions available for your monitor as detected by the driver. However, my guess is that you have already tried this...

Often, the reason higher resolutions are not available is that the card has not been detected properly, or that safe ones have been chosen because it has not been tested enough. When this happens, you can configure the server manually by typing the following into a terminal:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf-WORKING
```
(to back-up your current settings, then...)

```
sudo dpkg-reconfigure xserver-xorg
```

It will allow you to pick your card type, screen resolution range, etc. 


**IMPORTANT!** You are using an NVidia card, but i'm not sure if you have the restricted "nvidia" driver installed (see above post). To be safe, when the command above asks you for the card type, DONT PICK "nvidia"! Pick "nv" instead, which is definitely available on your system. After you have got this all working, you can set up the restricted driver afterwards if you decide to.

Once you have finished you will need to restart the computer for the changes to take effect (or alternatively restart the X-server by logging out and pressing Ctrl-Alt-Backspace)

You should find your chosen screen resolutions are now available in the 
System -> Preferences -> Screen Resolution utility after this.

Also, if you end up stuck at the terminal because your graphical display wont start, you can revert to your current setup by typing:

```
sudo cp /etc/X11/xorg.conf-WORKING /etc/X11/xorg.conf
```

and rebooting by typing "sudo reboot"

Good luck!


Write down the code before this

sudo cp /etc/X11/xorg.conf-WORKING /etc/X11/xorg.conf

---

### Post by reclusivemonkey on 2007-05-22
> **newboy12 said:**
> I'm currently running Ubuntu 7.04 at 1024 X 768 with a 17" Dell FP, I have a GeForce4 MX 240 and it is capable of getting much better resolution than this in xp. 

Is there are simple way (being new to linux) that I can increase the resolution as I don't wish to return to the dark side?

What resolution do you get in XP?

---

### Post by eks on 2007-05-22
Don't know how much knowledgeable you are on computers, but if SeanHodges solution doesn't work you can edit /etc/X11/xorg.conf and try to add a resolution on the Display section manually.

```

sudo gedit /etc/X11/xorg.conf

```


eks

---

### Post by lhuser on 2007-05-22
I'd got to Nvidia's site to obtain updated drivers. Then, it should work.
> **reclusivemonkey said:**
> What resolution do you get in XP?
His card can push 1280x1024 easily. The card itself can go to 2048x1536.

---

