---
title: "Beryl on dual monitors"
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by Seeker84 on 2007-05-24
So I still have some issues with dual monitor.  for one thing the external monitor likes to scroll in resoultion instead of a fixed space.  and window manager will not go into beryl it's stuck in metacity.  I have bindings that will only work with the beryl window manger active.  any thoughts?

---

### Post by krismatth3 on 2007-05-24
Are you using xinerama? I was under the impression that Beryl uses OpenGL, correct? And opengl will not work with xinerama.

---

### Post by Seeker84 on 2007-05-25
I don't know about the opengl thing.  but from what I can tell I have to use xinerama because I'm using an intel graphics card.

---

### Post by makhand on 2007-05-27
So is it impossible to have an Intel Integrated card running xinerama and beryl at the same time? Is there any other option to have 'xinerama-like' functionality but still be able to run beryl on an intel card? Thanks

---

### Post by Seeker84 on 2007-05-27
I don't know I'm still waiting for some more feedback.

---

### Post by Seeker84 on 2007-05-30
Still waiting for some help.

---

### Post by Seeker84 on 2007-05-31
Is anyone out there?

---

### Post by Seeker84 on 2007-06-01
Is anyone having the same issue?  Where you go to dual monitor and your keystokes in beryl aren't working? 
 
You can change this by right clicking the settings icon in the system tray and click "Select Window Manager" and then select one of the options there.  If your using beryl to mange you keystrokes select it and so on for the other options.  

In my experience I can't get beryl to stay in that Beryl Manager in dual monitor mode.

---

### Post by mijj on 2007-06-02
I've given up on Beryl ... it's pretty .. but ultimately uses up too much time if it doesnt work properly.

---

### Post by kakashi on 2007-06-02
> **mijj said:**
> I've given up on Beryl ... it's pretty .. but ultimately uses up too much time if it doesnt work properly.

really ?
i've fallen in love with the inpus zoom. i read on a lot of forums and like to sit away from my computer. input zoom is a god send for me. and who doesn't;t love wobbly windows and window wave?

---

### Post by Seeker84 on 2007-06-04
I'm not willing to give up on it.  I'm just waiting for another perspective to come by and help me out.

---

### Post by krismatth3 on 2007-06-04
Beryl + Xinerama = Will Not Work.

Xinerama screws OpenGL. It's a known problem. 

Beryl *requires* OpenGL.

Hence, Beryl + Xinerama will not work.

(Beryl + TwinView will work.)

---

### Post by Seeker84 on 2007-06-04
and twinview doesn't work on Intel, it works on nvidia, right?

---

### Post by krismatth3 on 2007-06-05
Correct, TwinView is nVidia only. (Although ATI has thier own thing.)

---

### Post by Seeker84 on 2007-06-05
I'm going to leave this post open.  If by chance in the future there is such a fix let it be posted here.  Until then, the determination of this thread is Xinerama doesn't with with Beryl.

---

### Post by RIVE on 2007-06-07
Ups, I just installed Xinerama, hope in Beryl 0.3 this will be fixed.:(

---

