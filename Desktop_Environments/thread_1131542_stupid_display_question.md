---
title: "stupid display question"
date: 2009-04-20
forum: Desktop Environments
---

### Post by SLEEPER_V on 2009-04-20
My problem is as follows.  I just installed ubuntu on my new system (dual boot) and I am using my sony bravia 40in tv as a monitor.  The edges of the desktop extend past the border of my tv.  Windows nvidia had a handy dandy screen sizer, but i can find one for ubuntu.  Of course I didnt add the 'handy dandy' to the search, so maybe thats the problem.

Resolution didnt matter 1280 or 1920 both had the edges of the desktop extended past the border. Help me ubuntu forums, you're my only hope.


btw running 8.10

---

### Post by sjprice on 2009-04-20
Look in System -> Administration -> Hardware drivers. You should have an option for installing the Nvidia drivers and settings config. 

Once installed, look in System -> Administration -> Nvidia X Server Settings and see if you can resize from there.

 Remember if you need to generate a new xorg.conf, you have to run Nvidia settings from teh command line with sudo privileges, or the changes wont stick.

---

### Post by SLEEPER_V on 2009-04-21
nope.  no go. that was actually the second place I had gone to try to straighten it out.  I even uninstalled and reinstalled them.

---

### Post by andrea000 on 2009-04-21
what card and driver version are you running?
nvidia drivers are in synaptic do you have 
the right one installed?Check to see and post 
back.

---

### Post by alpgucbilmez on 2009-04-21
Did you try to set the TV's zoom settings to full or 1:1 ? This might work too :)

---

### Post by SLEEPER_V on 2009-04-21
> **andrea000 said:**
> what card and driver version are you running?
nvidia drivers are in synaptic do you have 
the right one installed?Check to see and post 
back.

i'm using the integrated card on my mobo, nvidia nforce 560.  I installed the driver that was recommended I think it was the 180 as opposed to 177 or 173.  I'm a noob and all so I'll probably say about 10 stupid things, so sorry in advance.

---

### Post by SLEEPER_V on 2009-04-21
> **alpgucbilmez said:**
> Did you try to set the TV's zoom settings to full or 1:1 ? This might work too :)

tried it.  failtrain.

---

### Post by andrea000 on 2009-04-21
did you use [envyNG]("http://albertomilone.com/nvidia_scripts1.html") to install your driver?Try that unless that is the way you installed your driver i forgot what version of ubuntu you said you were running in 8.10 it's in synaptic and see what driver it says is preferred.

---

### Post by SLEEPER_V on 2009-04-22
> **andrea000 said:**
> did you use [envyNG]("http://albertomilone.com/nvidia_scripts1.html") to install your driver?Try that unless that is the way you installed your driver i forgot what version of ubuntu you said you were running in 8.10 it's in synaptic and see what driver it says is preferred.

i will.  Its a new build and I am having trouble getting it to recognize the wireless network too.  Just a series of hiccups that I guess is common to noobs, especially noobs on new builds.  Thank you for all the help thus far.

---

