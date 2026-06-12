---
title: "desktop eyecandy (compiz)"
date: 2011-03-26
forum: Desktop Environments
---

### Post by Stormy_shivers on 2011-03-26
first posting, if there is a mistake.. just remember first posting...  I have had several problems with activating the eye candy (compiz) I finally had it all figured out including the driver. work well for a week. till I activated the desktop cube and cube rotate.  I have decided I can live with out those but my minimize I chose (burn) will not work any more. I have reinstalled compiz extra plugins both my open and close (beam) and (Explode) work great. now for the odd part I have a dual screen system and everything works great on the primary screen. just the second screen is having the problem. ... Stormy

system specs
amd phenom II 6 core
ausu motherboard m4a89gtd pro/usb3
asus nvidia gtx460 graphics 1 gig
8 gigs gskill ram  
Running 10.04 64 bit

---

### Post by Krytarik on 2011-03-27
Welcome to the forums then!

Try resetting the settings in the "Minimize" tab of the "Animations" plugin in CCSM.

Greetings.

---

### Post by Stormy_shivers on 2011-03-27
thanks for the suggestion, but I had already tried that... unfortunately when I do try that i clears everything from the settings , I used the Beam settings that is my opening animation by copy and pasting them. but that didn't help in this case.. also remember this is a dual screen set up and the primary screen works just fine

screen specs
primary 20 LG
secondary 23 samsung

---

### Post by Krytarik on 2011-03-27
I know. I was hoping that Compiz manages to reset its settings regarding *both* at once. If you take a look into gconf-editor, path "/apps/compiz/plugins/animation/screenX", you should find settings for both screens. Since I don't know, which one is named by Compiz as "screen0" and "screen1" respectively, I didn't want to provide a command like this so far:
```
gconftool-2 --recursive-unset /apps/compiz/plugins/animation/screenX
```**EDIT:** If you run separate xscreens, as opposed to TwinView or Xinerama, you have to launch CCSM on the screen which has the issue (second) to change its settings. If you are using a TwinView/Xinerama setup, the described behaviour wouldn't make sense, because there were in my guess no separate settings.

---

### Post by Stormy_shivers on 2011-03-28
hey thanks very much for the help.. the screen that was having the problem was #1 and your code when adjusted for that, worked perfectly... now if you could tell me why when in enable the cube and rotation with 3d windows. it works perfectly until shutdown and when I reboot it is like it trashes my entire graphics my screen 0 had to be disabled then rebooted,.. ECT ect ect but as mentioned before I can live with out that part.  anyways thanks for sloving my problem posted...

---

### Post by Krytarik on 2011-03-28
No, not really. But you could try upgrading Compiz through their PPA, although the packages there are also quite old, you would get at least version 0.8.6, as opposed to 0.8.4 from the official Lucid repos.

---

