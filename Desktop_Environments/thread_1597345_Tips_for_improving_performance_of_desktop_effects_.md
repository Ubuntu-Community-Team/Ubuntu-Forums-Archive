---
title: "Tips for improving performance of desktop effects in KDE 4.5 (Kubuntu 10.10)"
date: 2010-10-15
forum: Desktop Environments
---

### Post by schnelle on 2010-10-15
Few tips for getting smooth desktop effects in KDE 4.5 :

1) Disable blur effect in System settings>Desktop effects>All effects.

2) Press Alt+F2 and type oxygen-settings. Then go to "animations" tab and uncheck "enable animations". Also under "Window decorations" uncheck "enable animations".

3) System settings>Application appearance>Style>Fine tuning tab. Choose "Low display resolution and low CPU"

4) System settings>Desktop effects>Advanced tab choose fastest texture filter.

5) If your desktop effect are disabled on every reboot then you'll have to disable functionality checks. Go to System settings>Desktop effects>Advanced and check "disable functionality checks".

6) If you are running opensource drivers (ati or intel cards) you could try to improve your desktop effects with updating your drivers from xorg-edgers ppa. If updated drivers doesn't work better, you could safely downgrade your drivers to official ones with ppa-purge comand. 
```
sudo apt-get install aptitude
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo aptitude update
sudo aptitude install ppa-purge
sudo aptitude safe-upgrade
```
Then reboot. If updated drivers do not work better you can downgrade them:
```
sudo ppa-purge ppa:xorg-edgers/ppa
```

7) You can upgrade KDE from 4.5.1 to 4.5.2. There are some kwin and oxygen style bug fixes which are improving desktop effects.

```
 sudo apt-add-repository ppa:kubuntu-ppa
sudo aptitude update
sudo aptitude safe-upgrade
```

This tips on my laptop improve performance and smoothness of desktop effects A LOT. Note that you should reboot after doing things from tips. I tried every tip my self so I am telling this from my personal experience :)
Have a nice and smooth desktop effects in great Kubuntu 10.10 release !!!  :)

Edit:
I just tried free radeon driver. Effects were very slow. Fix was to turn off vsync (I think free radeon driver has vsync always turned on. Even without vsync turned on in kwin desktop effects I had no tearing). So:

8 ) Go to System Settings>Desktop effects>Advaced and uncheck "Use Vsync ".

Cheers ;)

---

### Post by kio_http on 2010-10-15
Actually blur looks really nice! Best way to improve performance is go in Desktop Effects and make texture filtering fastest.

---

### Post by schnelle on 2010-10-15
> **kio_http said:**
> Actually blur looks really nice! Best way to improve performance is go in Desktop Effects and make texture filtering fastest.
Yes I agree it looks very nice but it is performance killer on my laptop and on few other PCs where I installed Kubuntu 10.10. Anyway I will add texture filtering to the tips :) Thanks for the tip :cool:

---

### Post by kio_http on 2010-10-15
> **schnelle said:**
> Yes I agree it looks very nice but it is performance killer on my laptop and on few other PCs where I installed Kubuntu 10.10. Anyway I will add texture filtering to the tips :) Thanks for the tip :cool:

Odd driver issue? Used to cause trouble for me in the KDE pre-releases but in 10.10 it works really speedy on my Intel GMA 945 64mb!

---

### Post by andreselsuave on 2010-10-21
Hey there!

The problem I have is that with the intel card of my mobo I could use OpenGL. However I bought a new video card:

Nvidia GT218 (Geforce 210) with 260 drivers

and now I am limited to Xrender. I also have tested some 3d action with games, and it is not performing as expected for a 1024mb card... I think there is a bigger problem than only the effects for me.

Can anyone help me? =)

---

### Post by inobe on 2010-10-21
> **andreselsuave said:**
> Hey there!

The problem I have is that with the intel card of my mobo I could use OpenGL. However I bought a new video card:

Nvidia GT218 (Geforce 210) with 260 drivers

and now I am limited to Xrender. I also have tested some 3d action with games, and it is not performing as expected for a 1024mb card... I think there is a bigger problem than only the effects for me.

Can anyone help me? =)

start a new topic in [multimedia and video]("http://ubuntuforums.org/forumdisplay.php?f=334") and someone will help.

---

### Post by boast on 2010-10-24
> **schnelle said:**
> Few tips for getting smooth desktop effects in KDE 4.5

thanks

---

### Post by baturay on 2010-12-10
Yeah, thanks a lot for the tips. My KDE is working faster now...

---

