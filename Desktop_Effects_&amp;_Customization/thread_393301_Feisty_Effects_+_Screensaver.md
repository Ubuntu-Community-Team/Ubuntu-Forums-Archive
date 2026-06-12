---
title: "Feisty Effects + Screensaver"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by Apreche on 2007-03-25
Hey, I'm using Fiesty on my new laptop, but there's a small problem. I'm not a fan of things like Beryl and whatnot, but I like activating the Desktop Effects because the drop shadows and such make looking at the screen easier on the eyes. The problem I have is that I use xscreensaver and electricsheep. The desktop effects work perfectly on their own, but they break the screensaver. 

Usually what will happen is the screensaver will display for a few seconds and then go black. I've tried different configurations of the electricsheep screensaver, and none of them seem to fix the problem. 

Is my only answer to wait for this feature to be less buggy?

---

### Post by powderhound99 on 2007-04-23
I'm having a similar problem i'm running beryl though. For the life of me i can't get them to run. All my dependencies have been filled and i ./config make and make install correctly but it just gives me 2 errors that i don't have time to reproduce at the moment but when i type electricsheep in it does nothing but run in the background it does the same as when i build a gui and run it. the curser drops below my path and doesn't respond. this tells me it's working but i'm not sure why it's not showing or dling sheep. this will be my fifth or sixth sys i'v installed on and it has allways been plug and go. Any ideas?

---

### Post by steeef on 2007-07-11
I thought I'd add my issue to this thread, as I too am trying to work out my issues with Xscreensaver (running ElectricSheep) and Feisty effects. When I lock the screen or let it go to screensaver on its own, one of two things happens:
1) I get a blank screen, even though I can tell ElectricSheep is running in the background (the fans spin up as it's generating new sheep).
2) ElectricSheep displays, but I get black rectangles where windows are open on the screen. For example, There's a nice big rectangle in the same position as the Firefox window I have open.

Any idea why this might be happening? I've checked Synaptic and I'm current on all packages.

---

### Post by steeef on 2007-07-11
Ah hah. I found the answer in another thread. In Beryl Settings Manager (under General Options, in the Advanced section), I checked "Unredirect Fullscreen Windows". ElectricSheep shows up fine now. Awesome.

---

### Post by markclewis1 on 2007-07-11
I changed my Beryl settings under the advanced tab, but my screen still goes black after some time.  The screensaver is running, if I swipe the mouse, the black screen goes away and there is the screensaver running underneath.  Is there some other setting I am missing?

---

### Post by steeef on 2007-07-11
Are you using gnome-screensaver or xscreensaver? I switched from the latter to the former, as ElectricSheep was designed with xscreensaver in mind. You could check your power saving options to see if there's anything like turning off the screen or showing a blank screen after a certain amount of time.

---

### Post by markclewis1 on 2007-07-11
I believe I am using gnome-screensaver.  I didn't change from the package that was installed with my Feisty, so I am assuming that is gnome.  I have checked all of my power management settings and I have everything set to 'never', except on battery power.  I will keep digging.

---

### Post by steeef on 2007-07-11
By default, gnome-screensaver restarts the screensaver after about 10 minutes. This may be causing your issue. I believe there is a way you can change this setting, but as I don't use gnome-screensaver, I don't know exactly where that is.

---

### Post by markclewis1 on 2007-07-11
I am not sure where it is either.  Maybe I will get lucky and someone else will weigh in with advice :)

---

