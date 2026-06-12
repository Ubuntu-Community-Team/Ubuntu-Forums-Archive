---
title: "Beryl Problem"
date: 2007-02-21
forum: Desktop Environments
---

### Post by panti19 on 2007-02-21
installed beryl using this tutorial
[http://wiki.beryl-project.org/index....tu/Edgy/nVIDIA](http://wiki.beryl-project.org/index....tu/Edgy/nVIDIA)
(automatic method)
and it doesn't start.
not even in XGL

i have the latest drivers installed using Envy
when i select in beryl manager (select window manager) Beryl , it doesn't load it. it remains set to Metacity

when i type:
beryl-manager in the terminal it opens the beryl right-click menu (the same menu that appears when i right click the gem).
and i see no errors whatsoever in the terminal

---

### Post by Sqwishy on 2007-02-21
Pleaase check your link, i'm getting a 404 error. Looks by the url that your using nvidia. Make sure your not using the legacy drivers, when you start beryl-manager from the terminal it should say checking for nvidia' and then 'found' or 'present' or something. if it does, that's good, and you probobly need to just right click on the beryl icon and make sure beryl is selected, not metacity, and reload the window manager.

---

### Post by panti19 on 2007-02-21
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

when i start beryl-manager (terminal):
ubuntu@panti-desktop:~$ beryl-manager
ubuntu@panti-desktop:~$ 
 it just opens the right-click menu, like i said
when i select the window manager "Beryl" in the menu, the window borders disappear for 1 second and then reappear with Metacity and it switches back to Metacity in the window manager menu.

---

### Post by panti19 on 2007-02-21
now i typed just "beryl" in the terminal and i get:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing

---

### Post by Sqwishy on 2007-02-21
google is your friend. A good way to fine answers is by googling the error. thats one of the nice things about linux is that there is verbose error output. 
I googled 'Checking for non power of two texture support : failed' and the first thing i got was a [http://pricechild.co.uk/?p=37](http://pricechild.co.uk/?p=37) try that fix!

---

### Post by panti19 on 2007-02-22
i google errors.
but to this i hardly found a fix.
in the link you gave me they all put problems , solutions and none of them states for which problem it is.
it's not organized

---

### Post by panti19 on 2007-02-22
help :( 
please

---

### Post by Sqwishy on 2007-02-22
if i were you i wouldn't of followed that guide. what graphics card are you using? specificly is it like a 6200 or a 7800 or what. If your using edgy try the following guide, it worked perfectly for my 7900gt ko 
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Also, is this just a recent problem like after a kernel update or has beryl never worked... O_o

---

