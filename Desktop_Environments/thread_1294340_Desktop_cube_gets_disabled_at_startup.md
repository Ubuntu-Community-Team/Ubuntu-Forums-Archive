---
title: "Desktop cube gets disabled at startup?"
date: 2009-10-18
forum: Desktop Environments
---

### Post by PHaLaNX on 2009-10-18
At every startup I have to go to systemsettings and disable/enable either desktop effects, or just desktop cube to get it working again. All other effects work fine. 

And also some of the desktop icons are missing at startup, I have to select them to make them visible. I don't know if it's related but it seems to have started at the same time with the cube problem. 

Anyone have an idea?

---

### Post by ssouthparkk on 2009-10-18
Are you funning Ubuntu from the Live CD or is it installed?

---

### Post by PHaLaNX on 2009-10-19
It's installed. I installed kubuntu-desktop over ubuntu 9.04, and installed ati drivers.

And also the "effect for desktop switching" option in desktop effects settings becomes "no effect" after restart.

---

### Post by ssouthparkk on 2009-10-19
I am actually very new to Ubuntu, but I think it might have something to do with your Compiz being compiled for Ubuntu, but you installed Kubuntu.  (Not sure of this, and I am most likely wrong.)

Try going into the package manager in administration and install the desktop-effects-kde.  I think it may be an issue with Gnome.  Not sure, maybe someone else can weigh in.

---

### Post by PHaLaNX on 2009-10-19
It's not compiz actually, I'm using KDE4's kwin desktop effects. Effects are all working fine, but the problem is as I said, I have to disable/enable the cube to get it working after each startup.

Thanks for trying to help though.

---

### Post by ssouthparkk on 2009-10-19
I didn't even know you could get a cube through other means without the use of Compiz.  Hmmm....

Yeah, well I better stay out of it.  I have a lot to learn on here.

---

### Post by PHaLaNX on 2009-10-20
Any ideas?

---

### Post by MelDJ on 2009-10-20
edit

---

### Post by Alex22 on 2009-10-20
Phalanx, do you use ATI Catalyst Control Center?

You could try going into Preferences> Startup Programs> Options (second tab) and ticking "remember..."

P.S. I didn't use the new KDE 4 much, but as i know, there is no other cube than Compiz cube. ;]
Even Bill's graphic system Aero can only look and admire.

It's just turning it on from kde settings.

---

### Post by PHaLaNX on 2009-10-20
I realized pressing CTRL + F1...4 shows the cube rotating so I thought there might be a problem with the shortcut. So I changed it, restarted and it's all working now. Turns out the problem was with the shortcut setting. 

Thanks to all who've answered. 

@Alex22

I believe it's KDE's own implementation of the compiz cube. Because I'm using kwin as the window manager. 

[http://digg.com/linux_unix/KDE4_KWin_has_new_Cube_plugin](http://digg.com/linux_unix/KDE4_KWin_has_new_Cube_plugin)

---

