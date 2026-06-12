---
title: "Installing nvidia driver = no more Xorg!"
date: 2009-02-22
forum: Desktop Environments
---

### Post by Selmer79 on 2009-02-22
I have an nVidia 9300/730i motherboard and a GeForce 9800GTX in my computer, and Ubuntu 8.10 runs just fine with the default open-source nVidia driver.

The problem comes when I try to install the closed-source driver from nVidia.

I've tried both the 177-driver from the repository and the 180.29 driver from nvidia.com, and both times they install fine but Xorg won't start once I reboot.

I'd like to get CUDA installed so that I can do GPU-boosted computing for BOINC, but I'm stuck atm..

Anyone know of a fix?

---

### Post by Rotaj on 2009-02-22
Just to get this question out of the way, did you try this command in a terminal window?
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by alexandari on 2009-02-22
Copy the output here when you try to start your X :}

also try rm /tmp/.X0-lock

and then startx        (I suggest you do it under root)

---

### Post by Selmer79 on 2009-02-22
@Rotaj: Tried that with FrameBuffer on and off, resulted in the following error when I ran startx:
```
Primary device is not PCI.
No devices detected.
No screens found.
```

@alexandari: No such file found.

I wrote down the error I get when I run startx with the default nvidia-generated xorg.conf from the 180.29 driver:
```
Failed to load module "type1" (module does not exist,0).
No devices detected.
No screens found.
```

I found no reference to any "type1" module in xorg.conf, so I'm stumped.

---

### Post by Selmer79 on 2009-03-04
Bump...

---

### Post by C-- on 2009-03-04
Did you try running

```
nvidia-xconfig
```

as root?

---

### Post by neppakyo on 2009-03-04
Also, 180.35 is avaialble. 

Im using it on jaunty

---

### Post by linfidel on 2009-03-04
Don't know if any of this will help, but I recently had problems getting Compiz and the restricted driver to work after it had worked for many different versions.  I was having problems with Firefox, where it would periodically freeze for 5 - 10 seconds, so I wanted to see if it worked better without Compiz.  I may have done the wrong thing, in that I ran "metacity --replace."

The upshot was that I couldn't get compiz or the restricted driver to run after that.  What I had to do was to use the system monitor to end the metacity process; but it was more complicated than that, because once I did that, I had problems opening programs and using the keyboard (mouse worked OK).  So, I had to do something like open the run dialog first, type in "compiz --replace", then stop the metacity process, and click on OK for the run dialog.  I think opening the restricted driver window would also work.

It's a longshot, but you can play around and try it.  It didn't seem to do any damage while I was playing around and repeatedly restarting X (Ctrl-Alt-Backspace).

---

### Post by darco on 2009-03-04
> **neppakyo said:**
> Also, 180.35 is avaialble. 

Im using it on jaunty

I wouldnt install 180.35 just yet, has a screensaver issue.....

darco

---

### Post by neppakyo on 2009-03-04
> **darco said:**
> I wouldnt install 180.35 just yet, has a screensaver issue.....

darco

I dont use screensavers, just monitor blank, and that works just dandy

---

### Post by hayalci on 2009-03-06
Hi,

You should edit the folowing file as root:
/etc/default/linux-restricted-modules-common 

And disable the nvidia modules that come with restricted drivers package.
DISABLED_MODULES="nv"

This prevents ubuntu from overriding the nvidia driver you have installed.
After a reboot, all should be fine if nvidia driver was installed correctly.

---

