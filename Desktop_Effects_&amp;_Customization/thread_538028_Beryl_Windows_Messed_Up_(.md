---
title: "Beryl Windows Messed Up :("
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by xValo87x on 2007-08-29
So i got beryl up and running, everything is great, only thing is this....

[img]http://xs218.xs.to/xs218/07353/hi2ulollove.png[/img]

Any suggestion's?

I tried: 
```
emerald --relpace
```

and I also tried restarting beryl etc..

Thanks,
~Valo

---

### Post by ExXxTaZi on 2007-08-29
you didnt installed any theme,install with this:
 sudo apt-get install beryl beryl-manager emerald-themes
or with synaptic,and go to system tools-beryl manager-emerald theme manager and pick a theme..

---

### Post by Inxsible on 2007-08-29
There might be a few things wrong

1) Your graphics card. But this is less likely considering that you can at least run Beryl.
2) Try ```
metacity --replace
``` If that brings the borders back, then Beryl is the problem.
3) Lastly, Beryl has now merged with Compiz to become Compiz Fusion. If you want, you can try to uninstall Beryl completely and install Compiz Fusion.

---

### Post by xValo87x on 2007-08-29
That brings back the borders. So then Im assuming that Beryl is the problem... /sigh it seemed to be running finally >.>

Anyways I tried to get compiz fusion, and I already have my gfx card setup and what not w/ my xgl session. Its when I try to get compiz fusion... i use this code:
```
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
```

but i get back this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
E: Couldn't find package compizconfig-settings-manager

```

Now according to the thread here ([http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz&page=24](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz&page=24)) a few posts down, someone states that on the x64 version i need to have a certain rep.
> There's a line or four in your /etc/apt/sources.list for: 3v1n0's eyecandy repository, should be something like download.tuxfamily.org/3v1n0 or something.

Is it set to eyecandy-amd64 on the deb lines? 

Now i changed the line to say that, here is my rep list:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
[B]deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd6[/B]4
```
 The lines used to state "deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy &&
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecand"

I only added the -amd64 like it was on the post, however, i dont think its correct because im still getting the error.  

So im at a loss /sigh... cant seem to get beryl or compiz to work right.

---

### Post by cudaman73 on 2007-08-29
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

Try the repos from that guide.

Follow a how-to here on the site to show you how to completely remove any traces of compiz/beryl (assuming you haven't already), and then follow that guide.

Worked for me, on a 64-bit system.

---

### Post by xValo87x on 2007-08-29
Well i followed that, and it seems that I got compiz-fusion and what not, but i still cant get the setting's manager.  It only seems to want to run off metacity theme's as well too. 

It does have one config. tool Compiz GL Deskop? Thats what im using now... but it dosent seem right... /sigh

---

### Post by xValo87x on 2007-08-29
Thanks for that guide ^-^

Got it all working yay! FINALLY! LOL!

---

