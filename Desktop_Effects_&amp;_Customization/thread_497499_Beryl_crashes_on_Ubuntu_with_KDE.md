---
title: "Beryl crashes on Ubuntu with KDE"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by punky on 2007-07-10
I started off with Ubuntu but wanted to switch to KDE. I followed the guides and have it installed. I tried to remove Gnome using apt-get (remove ubuntu-desktop, autoclean, etc) but it still persists.

Anyway, I can boot into KDE fine. If I try and switch to Beryl, it crashes. However if I select the launch fallback, it runs metacity, which is Gnome isn't it? Still runs with the KDE menus.

When I run beryl-manager or beryl,it says > Detected xserver                          : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
. 

So it looks like I am running AIXGL instead of XGL, although I thought I installed and ran XGL(xserver-xgl is installed with apt-get). it says "direct rendering: Yes" when I do "glxinfo | grep direct" flglrxinfo shows my graphics card (ATI)

I have seen someone I should be apt-getting the beryl-kubuntu package, but it doesn't exist in the repositories?

I've tried removing and re-installing beryl, but its no different.

Any suggestions as to where to go from here?

Many thanx in advance.

---

### Post by Happy_Man on 2007-07-10
You have to manually choose "xgl" from the sessions menu before you log in. Perhaps that is your problem?

---

### Post by punky on 2007-07-10
Cheers mate.

If I select Xgl at login, then it boots into gnome, with beryl working.

Do you know how to force it to boot into KDE?

Here are my xgl startups...

/usr/local/bin/startxgl.sh
> 
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
#exec gnome-session
exec startkde


and

/usr/bin/startxgl.sh
> 
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLA$
# Start KDE
exec startkde


But gnome still boots?

---

### Post by Happy_Man on 2007-07-10
ummm.... I, unfortunately, have no idea. I just install the Nvidia driver for my card through a simple ```
sudo apt-get install nvidia-glx
```, restart X, and log in as normal. Then everything works. I'm not sure how to work with XGL, though.

---

### Post by punky on 2007-07-10
Hurrah, I got it working :)

I figured that if xgl keeps booting into gnome, I must be altering the wrong startup script or something. Did a search and found there was one, startxgl (no.sh extension), with gnome-session in it. Commented it out put in startkde in there and bingo. KDE with Beryl :)


Thanx for the help HM.

---

### Post by Happy_Man on 2007-07-10
Congrats. Have fun!

---

### Post by punky on 2007-07-10
Me again! (sorry...) but, its not letting me off that easily..

Beryl is working, but its booting in metacity by default... 

When it boots you can see the 4 desktop screens, btu then as soon as the beryl emerald logo appears, it switches to two desktop screens. I can select beryl and it runs fine...

Its not the end of the world, but is a bit annoying. I can't seem to find any command or anything to force it to use beryl window manager (as opposed to metacity) by default.

Sorry to keep bugging you guys with this...

---

### Post by Happy_Man on 2007-07-10
Go to System --> Preferences --> Sessions, startup programs, and add the following two entries:

```
Name: Beryl
command: beryl-manager
```

and

```
Name:Emerald
Command: emerald --replace
```

Should do it!

---

### Post by punky on 2007-07-11
Cheers mate,.,

Its gets weirder though...

Powering up this morning, I noticed it beryl was selected. Restarted, and it was metacity. Did it a few more times and it just seems completely random.

I've added what you said though, so hopefully it should work all the time now. Computers eh?

Thanx again HM  =D>   :)

---

