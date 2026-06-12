---
title: "can someone help me with beryl??"
date: 2007-02-06
forum: Desktop Environments
---

### Post by MyNameUhBorat on 2007-02-06
Hey everyone I've had the latest beryl installed on my Dell laptop for the last week or so, and I've been trying to tinker with the settings in order to get those amazing desktop cubes that people have, but I just can't seem to figure it out. I've looked through the forums here and on beryl's official site, but I couldn't find anything but guides on howto install it rather then how to use it. Can someone give me a little bit of help because I've done my homework and I'm still unable to figure it out.:) 


Thanks in advance everyone,

Jeremy

---

### Post by shareMenaPeace on 2007-02-06
Which Dell Model Number is it?

---

### Post by Metlin on 2007-02-06
Can you give some more details?

What version of Ubuntu? What model laptop? What model video-card etc?

More information the better.

---

### Post by MyNameUhBorat on 2007-02-06
Sorry, I knew I left something out. It's a Dell Inspiron 6000 with Intel 915. I'm running Edgy right now.

---

### Post by shareMenaPeace on 2007-02-06
Oops, i thought you need install helps :)

Well for settings i can say, 
Use blure effects but use the settings only on minimum value or you end upp with a blured out screen :)

And here is a list i can recommend for settings.

```
Recommended Beryl Settings
Create under "General Options" -> "Settings and Profiles" new profiles, just incase settings get messy.

Desktop -> Rotate Cube -> Behavior -> max. "Zoom"
Desktop -> Desktop Cube -> Caps - add here your own *.png images and choose "scale".
Desktop -> Desktop Cube -> Skydome - add here a overall backgrround wallpaper *.png and animate it.
Desktop -> Desktop Cube -> Trancparency "enable"

Visual Effects -> 3D Effects -> enable "3D Effects" and window depth.
Visual Effects -> 3D Effects -> enable "Blur Effects"

Extras enable "Screenshot"

Recommended Emerald Theme Manager Settings
Choose a nice window theme.
```

And correct me if im wrong but i think what you search is how to access the cube mode (SHORTCUT).
This can basicly set in the general options panel in beryl settings manager.

The default CUBE VIEW is "middle" mouse button click and hold to zoom out....(click on desktop)

Constant Cube Mode (click on desktop)
ALT + STRG and click middle mouse button.

ALT + STRG "page down key" - diffrent view.

ALT + STRG + TAB access window slider

ALT + STRG + right or left KEY move cube.

Move mouse right corner of screen to slide active windows "window switcher - preview mode"

To access teh beryl manager typde in terminal
> beryl-manager
or use Applications -> System Tools -> Beryl Manager
or use Beryl Icon right top of screen.

cheers

POSTED here in REINSTALL BERYL GUIDE aswell.
[http://ubuntuforums.org/showthread.php?t=354228](http://ubuntuforums.org/showthread.php?t=354228)

---

### Post by MyNameUhBorat on 2007-02-06
Hey thanks a lot man. I just used your guide to uninstalling and re-installing beryl and followed the rest of your guide. My first time installing it I never even thought of creating a 2nd profile so if anything wrong I could just go back to default settings. But now I can't seem to get my image on the top or bottom of the cube. Any thoughts of what I'm doing wrong?

Thanks again

---

### Post by shareMenaPeace on 2007-02-07
> **MyNameUhBorat said:**
> Hey thanks a lot man. I just used your guide to uninstalling and re-installing beryl and followed the rest of your guide. My first time installing it I never even thought of creating a 2nd profile so if anything wrong I could just go back to default settings. But now I can't seem to get my image on the top or bottom of the cube. Any thoughts of what I'm doing wrong?

Thanks again
Nice np, 
delete the old caps images, highlight and use the "-" button.

---

### Post by MyNameUhBorat on 2007-02-07
Ya I tried that and it still stays on the default cubecaps. Also how do I change the background for when I go into cube mode?

---

### Post by shareMenaPeace on 2007-02-07
Did you used a PNG image?
And this image can be changed in SKYDOME check the link to the beryl reinstall howto i posted above.

Cheers

---

### Post by MyNameUhBorat on 2007-02-08
When ever I go into cube mode and switch the to another desktop the background is the same color as the skydome. The original desktop is fine then when I swtich it changes and I can't see the desktop icons.

---

### Post by shareMenaPeace on 2007-02-08
> **MyNameUhBorat said:**
> When ever I go into cube mode and switch the to another desktop the background is the same color as the skydome. The original desktop is fine then when I swtich it changes and I can't see the desktop icons.

You mean the desktop icons are gone  for your gnome/kde session??
Or do you mean when you in cube mode you dont see the desktop icons - but they are back when you leave cube mode?

Maybe you mean cube -> transparency?

---

### Post by MyNameUhBorat on 2007-02-08
It's for my gnome session. I swear by gnome :). transparency is off. It happens when I switch to another desktop. The wallpaper is gone and I can't see the icons. I've been trying to fix it but can't seem to do it. BTW thanks for all your help man.

---

### Post by shareMenaPeace on 2007-02-08
MAybe you enabled under

General Options -> Desktop Background -> Desktop Manager supports viewports?

This just displays 1 desktop and leaves the 3 other "cube" sides "clean".

---

### Post by MyNameUhBorat on 2007-02-08
Wow what do you know it sure was enabled. lol

---

### Post by shareMenaPeace on 2007-02-08
I think that can be used to display 4 diffrent wallpaper or screensaver on the other sides...but maybe just in KDE ...dont know :)


Cheers

---

### Post by Metallinut on 2007-02-09
Hey I've got a stupid question...

I've got Beryl up and running again (0.1.99.2) and I was futzing around with the settings (rookie mistake) and my cube is messed up...

It appears to just be a two-dimensional square.  If I use the mouse to rotate the 'cube' it looks more like 1 plane...in other words, once half-way rotated, the screen disappears, much like if you look at the 'side' of a piece of paper.

If I try to rotate up and down, things get really strange...

All in all, my cube turned into just one 'side' which I can rotate around, but there is no cube!  

I've been looking through all the settings, but can't seem to locate it.  If I just delete my settings in my home directory, would beryl default back to the original settings?

Thanks,

---

### Post by shareMenaPeace on 2007-02-09
Basicly make diffrent profiles - keep the default clean.
Some plaugins or slightly diffrent settings can lead to beryl crashes.

What you need i think is

General Options -> Virtical Virtual Sice (should be 4 for a cube).

---

### Post by MyNameUhBorat on 2007-02-16
Bery put icons on my desktop but I can't seem to remove them. Any idea of how I can get rid of them?

---

### Post by MyNameUhBorat on 2007-02-21
Everything opens in the background as well. Also using this as a polite bump

---

### Post by Metallinut on 2007-02-21
So I saw on the roadmap at [http://www.beryl-project.org](http://www.beryl-project.org) that Beryl 0.2 final should be out by now.  But on [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) it still looks like 0.1.99999 whatever.  

Any word on when 0.2 final will be in this repo?

---

