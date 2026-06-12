---
title: "Ready for special effects?"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by geovino on 2007-11-22
I have Ubuntu 7.10 installed and the basic special effects run fine. I have a nvidia geforce 6200 card. If I add compiz manager do you think I'll be able to run the other special effects like the cube? If it doesn't work can I go back to the regular effects without messing up the screen?

---

### Post by oedipuss on 2007-11-22
I think it's very safe to try it, since you can already run basic effects without problems. There's not much difference between basic and advanced, with the exception perhaps of some shader support for blurring. In any case, a nvidia 6200 should be more than enough, and I think  the desktop automatically reverts to basic settings or no effects at all if for some reason it can't enable the advanced ones.

---

### Post by Forlong on 2007-11-22
As long as you don't enable resource intensive plugins like blur you will be fine. Cube will definitely work.

---

### Post by geovino on 2007-11-22
Thanks. I installed gnome-compixz-manager and x-glx. Rebooted. Now where do I go to set up the effects like cube and others?

---

### Post by guitarguy987 on 2007-11-22
> **geovino said:**
> Thanks. I installed gnome-compixz-manager and x-glx. Rebooted. Now where do I go to set up the effects like cube and others?

You can go to System -> Preferences -> Advanced Desktop Effects Settings to enable things like cube, wobbly windows, etc...

---

### Post by acoustic-alchemist on 2007-11-22
Being a pretty new user I'm not sure what im doing wrong. Got the basic effects working ok, but the compizconfig settings manager wont load at all. Upon entering compiz in a terminal I get the following:

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Eep?!

---

### Post by geovino on 2007-11-22
Its working fine... very cool! :)

---

### Post by acoustic-alchemist on 2007-11-22
I still cant get any wobbly windows or cuboids on the go. Ive got compiz settings manager from synaptic now. I long for the wobble!

---

### Post by jimerickso on 2007-11-22
> **acoustic-alchemist said:**
> Being a pretty new user I'm not sure what im doing wrong. Got the basic effects working ok, but the compizconfig settings manager wont load at all. Upon entering compiz in a terminal I get the following:

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Eep?!

i get that warning too. i have been told not to worry about it. seems to work ok.

---

### Post by acoustic-alchemist on 2007-11-22
Hi jimerickso, thats cool - thanks. How did you get your wobbly windows / cube to work?
Am I doing something obvious wrong?! XD

---

### Post by geovino on 2007-11-22
Did you install gnome-compiz-manager from synaptic?

---

### Post by Forlong on 2007-11-23
> **acoustic-alchemist said:**
> How did you get your wobbly windows / cube to work?
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) :)

Oh, and please do not install gnome-compiz-manager. It's not designed to work with Compiz Fusion. So you will miss lots of options and it could interfere with ccsm.

---

### Post by geovino on 2007-11-23
> **Forlong said:**
> See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) :)

Oh, and please do not install gnome-compiz-manager. It's not designed to work with Compiz Fusion. So you will miss lots of options and it could interfere with ccsm.

Then what are you supposed to install? I was told to install gnome-compiz-manager and its working fine for me. Is there a wiki or thread that tells you what you should have to run special effects?

I've also noticed that the screensaver doesn't work anymore. is that normal?

---

### Post by Forlong on 2007-11-23
> **geovino said:**
> Then what are you supposed to install?
CompizConfig Settings Manager (ccsm), just follow the link.

---

### Post by jimerickso on 2007-11-23
@acoustic-alchemist

well at the risk of sounding stupid i will cover some of the basics.
go to system > preferences > advanced desktop settings (or compizconfig settings manager)
got to general options > desktop size tab
set the following
horizontal virtual size 4
vertical virtual size 1
number of desktops 4
make sure desktop cube is enabled
make sure rotate cube is enabled
make sure wobbly windows is enabled

let me know how it goes. good luck.

---

### Post by geovino on 2007-11-23
Mine is working here in Gutsy, but I'm trying to get it set up in Mint 4.0 on my other pc. It has wobbly windows and when I click on the desktop incons on the task bar the window rotates, but it doesn't rotate by rolling the scroll wheel on the desktop like it does in Ubuntu and I can't rotate the cube by holding down both mouse buttons like I can in Ubuntu, what am I missing?

---

### Post by acoustic-alchemist on 2007-11-27
Hmm, I tried that guide but it still seems to be not functioning correctly. I still get that error in terminal when I run ccsm. Well at least I have the basic effects - for the meantime anyway :D Thanks!

---

