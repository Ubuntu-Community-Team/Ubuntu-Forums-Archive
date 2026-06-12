---
title: "Since today: Xserver crashes when screensaver comes alive"
date: 2007-04-04
forum: Desktop Environments
---

### Post by robenroute on 2007-04-04
Hi there all,

As of today (I did do an update today: Xorg?), as soon as my Gnome Screensaver kicks in, the Xserver crashes and throws me back to the login screen.

Anyone knows what's going on?

---

### Post by Calin on 2007-04-04
Hey,

i've go the same issue since today after some automaticly updates for the X-Enviroment. My idea to fix for a while: Turn off the screensaver, but if i open the screensaver panel gnome crashes,too.

I hope i'll get a fix tomorrow or a nice workaround to clean it by myself ;-)

gp
calin

---

### Post by robenroute on 2007-04-04
> **Calin said:**
> Hey,

i've go the same issue since today after some automaticly updates for the X-Enviroment. My idea to fix for a while: Turn off the screensaver, but if i open the screensaver panel gnome crashes,too.

I hope i'll get a fix tomorrow or a nice workaround to clean it by myself ;-)

gp
calin

Hi Calin,

I know, I just tried switching the screensaver off and Xserver just crashed..... It must be that a lot of people suffer from this.

I'm looking forward to a very quick fix!

Thanks,
Rob

---

### Post by magnus.gylfason on 2007-04-04
Is your screensaver using opengl? If so, its probably the nvidia driver. I had to install the nvidia-glx module again.

---

### Post by MoonBlossom on 2007-04-04
I'm having the same problem. 

I tried to turn off my screen saver but my system crashed. It's there anyway I can turn off the screen saver from the console?

---

### Post by el mariachi on 2007-04-04
I can't any hardware accelerated app. games or whatever, they all restart X. now i remember, I also did those updates...

there is a nvidia-glx binary in the repos but I installed the drivers through a guide from the forum that didn't use the repos... if we install both they would conflict right?

---

### Post by MoonBlossom on 2007-04-04
I reinstalled the nvidia drivers using envy and my system got fixed :guitar:

---

### Post by el mariachi on 2007-04-04
> **MoonBlossom said:**
> I reinstalled the nvidia drivers using envy and my system got fixed :guitar:

worked for me too, thanks :KS

---

### Post by robenroute on 2007-04-04
> **el mariachi said:**
> worked for me too, thanks :KS

And me.... Thanks a bunch.

I guess that every update of the kernel AND xorg means reinstalling the nVidia driver. Ah well, with people like tseliot and his howtos around, that shouldn't prove too difficult.

Thanks everyone!

---

### Post by twl on 2007-04-04
I fixed this without reinstalling the nvidia driver.  Try the following first:

cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

---

### Post by Bad_Byte on 2007-04-04
> **twl said:**
> I fixed this without reinstalling the nvidia driver.  Try the following first:

cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

Thanks that fixed it for me as well =)

---

### Post by FuturePilot on 2007-04-04
Hmm, this is interesting, a few months ago this same thing happened to me but I wasn't using the Nvidia drivers. It happened immediately following an Xserver update. Wine would crash X so would the screensaver, glxgears, OpenOffice, glxinfo, just about everything. It seems to me that they have a problem implementing Xserver updates whether you're using the proprietary Nvidia driver or not. They need to do something about this as my solution was to do a complete reinstall:( I though it might have been a fluke or something but now that I see it is happening again and to a lot of people.... This is a serious problem and needs to be addressed.

---

### Post by eeefresh on 2007-04-05
I was having the same problems as everyone else tonight.  My screensaver would reset xorg.  However, when I reinstalled the nVidia drivers via envy, I had some new problems.  The screen saver no longer reboots my session, but now most of the screensavers don't work.  I am also getting a "failed to initialize HAL" message on boot up.

Any suggestions?

---

### Post by ronnieredd on 2007-04-07
cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

This fixed mine too.:popcorn:

---

### Post by skip27 on 2007-04-08
> **twl said:**
> I fixed this without reinstalling the nvidia driver.  Try the following first:

cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

Also worked for me. Thanks!

---

### Post by willz_2 on 2007-04-12
> **twl said:**
> I fixed this without reinstalling the nvidia driver.  Try the following first:

cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

appreciate this big time......i also had to reboot afterwards...

---

### Post by tophe on 2007-04-12
same to me. tks

---

### Post by perisarc on 2007-04-15
i did what twl did and it worked for me. its all good now. i guess something overwrote that file during the update. but you have to reboot after you copy the file for it to take. i tried it three times before it hit me i might need to reboot. (im a linux noob)

thanks twl, excellent.

---

### Post by Hilko on 2007-09-12
> **twl said:**
> I fixed this without reinstalling the nvidia driver.  Try the following first:

cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

No clue whatsoever what this has done or why it works, but it did. Thanks! Only thing is that in the preferences -> screensaver menu some of the previews don't work. They just show a blank screen. But fortunately not all of them, so I can use my screensaver again.

---

