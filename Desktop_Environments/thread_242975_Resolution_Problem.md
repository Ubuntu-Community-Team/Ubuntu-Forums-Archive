---
title: "Resolution Problem"
date: 2006-08-24
forum: Desktop Environments
---

### Post by azraelx401 on 2006-08-24
I just installed Ubuntu and the only resolution i can get is 1024x768.  I have a wide screen laptop and things don't look right.  Can somebody help me so I can get better resolution on this?

---

### Post by LeftyAce on 2006-08-24
First, to get full resolution out of your video card you'll need to install the proper drivers.  What kind of video card does the laptop have?

You can try the following without new drivers, and it will be necessary even with them.

```
sudo gedit /etc/X11/xorg.conf
``` 

Look for the section titled "Display." You should see (among other things) lists of resolutions.  Something like
```
"1024x768" "800x600" "640x480"
```

Everywhere you see such a list, add the desired resolution to the BEGINNING.  the X system starts at the left and uses the first resolution that works.  There are multiple sections, each corresponding to (I think) different run states, color depth, etc.  Just add your resolution everywhere you see other resolutions, and you should be good.

Let us know what video card you have, so you can get the proper drivers. That will help with high-res stuff and especially anything 3D.

---

### Post by hraposo on 2006-08-24
Try it:
sudo dpkg-reconfigure xserver-xorg

---

### Post by azraelx401 on 2006-08-24
thanks for the help, the laptop has the Intel 915 GM card.  I tried the sudo gedit /etc/X11/xorg.conf and i saw the display that said what I want it to say but when I go to the resolution application it only shows 1024x768

---

### Post by azraelx401 on 2006-08-24
> **hraposo said:**
> Try it:
sudo dpkg-reconfigure xserver-xorg

i tried this too but i messed up the set up and had to install ubuntu over again.

---

