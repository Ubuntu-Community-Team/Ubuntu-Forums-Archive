---
title: "question about Beryl - Core Dumped???"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by kystorms on 2007-05-14
I have been running beryl fine as can be, and all of a sudden today it crashes and this is the code i get when i type beryl in the terminal -
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
libpng error: Read Error
Aborted (core dumped)
lisac@lisac-desktop:~$ 

Can someone explain what that last few lines means, and how I can go about fixing it? if that is possible I mean.
I love it, and have no problems what so ever before this, so this is strange. I dont use a session to run Beryl, i just click the Beryl icon in Applications and then change the window manager to Beryl from the Red Icon on the tool bar where it says select windows manager.

Thank you very much to anyone who can help

:( :confused:

---

### Post by kystorms on 2007-05-14
as an add on, I went in and turned off the window decorator, turned beryl off and then back on, then turned the decorations off, then after beryl began running again, I ran this in terminal to check 
"beryl"
and this is the out put now
lisac@lisac-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
beryl: Plugin 'showdesktop' can't be activated because plugin 'fadeDesktop' is already providing feature 'showdesktop'
Couldn't initialise showdesktop. This should not happen!
No framebuffer_object support! (only simple Blur aviable).
No fragment_program support! (only simple Blur aviable).
X connection to :0.0 broken (explicit kill or server shutdown).
lisac@lisac-desktop:~$ 

I am not sure where to go now, or what to either turn off or on. Beryl is running, but obviosuly there is a problem so, I would like to fix if possible.

thank you:confused:

---

### Post by dfreer on 2007-05-18
try this out:
[http://forum.beryl-project.org/viewtopic.php?f=37&t=5675](http://forum.beryl-project.org/viewtopic.php?f=37&t=5675)

EDIT:
also, go into beryl-manager and disable whatever is calling this file:
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg

I'm guessing it is your skydome image. skydome images have to be a certain resolution in order for them to work, and they crash a lot in my experience. find one that looks good and works and stick with it lol!

---

