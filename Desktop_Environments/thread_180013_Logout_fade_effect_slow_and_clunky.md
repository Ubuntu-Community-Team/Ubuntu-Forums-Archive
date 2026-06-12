---
title: "Logout fade effect slow and clunky"
date: 2006-05-21
forum: Desktop Environments
---

### Post by teppic on 2006-05-21
When logging out, the fade effect looks really unimpressive for me. It's not at all smooth and looks like it's a quick unofficial hack.

Is this just happening for me or everyone? I'm using a decent nvidia graphics card (6600GT) and get the same whether I'm using the open source or the proprietary drivers.

Compared to the smooth logout effect in Suse 10.1, this looks really amateurish.

---

### Post by abs on 2006-05-21
i would have to agree with you on that, they are slow and dont look very pro, is there a way of disabling them or at least improving the effect, it would be nice it was smoother and les clicky and chunky, i would rather laike to say no fading, just a quick fade.

what i mean is that when i am asked for a password i dont wont to get the fading in the background, just a simple one gray frame - none progressive,

would be better i think

---

### Post by vyruss on 2006-05-21
[QUOTE=abs]i would have to agree with you on that, they are slow and dont look very pro, is there a way of disabling them or at least improving the effect, it would be nice it was smoother and les clicky and chunky, i would rather laike to say no fading, just a quick fade.
what i mean is that when i am asked for a password i dont wont to get the fading in the background, just a simple one gray frame - none progressive,
would be better i think[/QUOTE]

I do like the effect as eye candy, but our (ubuntu's) implementation of it is quite ugly, not smooth at all. Moreover, the last frame of the animation when you enter the password and it goes back to normal colours looks like a screen redraw and is quite unprofessional... :(

---

### Post by henriquemaia on 2006-05-21
I'm with you guys. And my graphical card is not that bad. Is there a reason for this?

---

### Post by jak on 2006-05-21
It's even worse for me, I have fairly low-end graphic cards (Radeon 9200SE's) and running 2 or 3 screens. It's very slow, and there's no simple way to turn it off.
Same as running gksudo.

---

### Post by Lord Illidan on 2006-05-21
I agree.

---

### Post by denzilla on 2006-05-21
I'm running an old Ati Rage card and the fade effect looks like a slide show, with some white blocks at the end. I'd rather not have it if it looks like this. The wireframe crap when minimizing/restore needs to go to.

---

### Post by Lord Illidan on 2006-05-21
That wireframe crap is part of Metacity. Horrible.

---

### Post by abs on 2006-05-21
[QUOTE=Lord Illidan]That wireframe crap is part of Metacity. Horrible.[/QUOTE]
true, totally useless and crap effect, it reminds me of windows CRAPY EFFECTS, just keep it simple, minimise with out that effect, don't need it in ubuntu at all.

all these effects make the system look slow and un-pro. i think it should be taken off of simplified even more, no need for transitions.

I think if you are gona include eyecandy then do so if it is 100% good otherwise it will backfire and just look taky.

---

### Post by monchichi on 2006-05-21
I filed a bug about this a long time ago:

[https://launchpad.net/distros/ubuntu/+source/libgksu1.2/+bug/5970](https://launchpad.net/distros/ubuntu/+source/libgksu1.2/+bug/5970)

---

### Post by Delkster on 2006-05-21
[QUOTE=abs]minimise with out that effect, don't need it in ubuntu at all.[/quote]
It's not pretty but it does serve a purpose: it shows where in the window list the minimized window appears.

I guess the praised technological advances which are coming should allow for a better effect for that.

[edit] slight fix

For me the fading effect on logout is decent although not completely smooth. I have an Athlon XP (~2 GHz), Radeon 8500 (R200, open-source driver) and a CRT monitor. On the other hand, on my parents' Duron (~1 GHz), equipped with a GeForce 2 using the proprietary NVidia driver and a cheap TFT monitor it's rather jumpy.

---

### Post by teppic on 2006-05-21
Yes - when it comes back from a password prompt it looks particularly bad.

I was hoping this clunkiness would just be something in the development stage but it's looking like this will go into the final release, which is sad when the rest has been polished as it does look very unimpressive, especially for people coming from XP where the fade out is much more professional.

---

### Post by Gabriev on 2006-05-21
Is it possible to disable the effect? :confused: 
I hope the team will fix it before final release! :(

---

### Post by teppic on 2006-05-22
I don't think it's possible to disable the effects. I've got a vague hope that they've got something that works properly in testing that will be out with the release candidate. I hope...

---

### Post by hornett on 2006-05-22
It's smooth in terms of FPS for me, but looks like it's doing some low quality dithering, since the colours get banded and 'trippy' looking for want of a better word... :o 

If only x composite was stable and enabled by default, the fade effects could be written easily by simply altering the transparency of a large, dark coloured window and it would be hardware accelerated automatically on drivers supporting it properly.

---

### Post by jonny on 2006-05-22
I believe that this is an issue with the extremely poor 2D acceleration provided by the nVidia drivers.  On my laptop (very low quality integrated Intel graphics), the fade out is silky-smooth.  I've set up 4 other PCs with nVidia graphics and the effect is always horribly clunky.

The issue is more pervasive than the fade-out effect.  Try dragging a window around (without XGL enabled) or scroll rapidly in Firefox and look at your CPU usage.  With an nVidia card, it'll be near 100%; with cheapo Intel integrated graphics, it'll be much lower.

The trouble is that, with proprietary drivers, no-one is able to fix the problem.  And it seems that nVidia itself can't be bothered.  There are many other threads on this subject, but I've never seen a satisfactory resolution.

---

### Post by teppic on 2006-05-22
The problems occur with the Nvidia open source drivers too - not just the proprietary ones.

Also, in Suse 10.1 on this computer, the logout effect is a really smooth desaturation to greyscale, and looks absolutely fine.

---

### Post by graigsmith on 2006-05-30
these effects should be disabled. or at least they should let you disable them. 

they are buggy, and don't look nice on my ati 9200 with open source drivers.  and it's causing problems with me being able to play games. the screensaver will come on  and start fading during tremulous.

---

### Post by garretwp on 2006-05-30
I would have to agree, I would like an option to disable this effect. I run freenx and when you go to logout, it slows the whole log out process when your running in a freenx environment as it tries to draw the fade effect and does not do it well.

Garrett

---

### Post by henriquemaia on 2006-05-31
[quote=graigsmith]these effects should be disabled. or at least they should let you disable them. 

they are buggy, and don't look nice on my ati 9200 with open source drivers.  and it's causing problems with me being able to play games. the screensaver will come on  and start fading during tremulous.[/quote]

That screensaver problem also happened to me. I friend of mine was playing Frozen-Bubble on my computer and then the screen started to fade. I had to turn off the screensaver for her to play without interruption.

---

### Post by reh4c on 2006-05-31
Believe it or not, the fadeout looks great on my Fujitsu subnotebook with a ATI Rage Mobility P/M video chip.  However, coming out of hibernation, the two "pixelated boxes" before the login screen look very clunky...just a blank screen would be better.

---

### Post by henriquemaia on 2006-05-31
[quote=reh4c]Believe it or not, the fadeout looks great on my Fujitsu subnotebook with a ATI Rage Mobility P/M video chip.  However, coming out of hibernation, the two "pixelated boxes" before the login screen look very clunky...just a blank screen would be better.[/quote]

Probably yes. It was good to have some way of trying this.

---

### Post by XQC on 2006-05-31
Still, why does Suse manage to have a smooth transition with nvidia cards and Ubuntu does not?

---

