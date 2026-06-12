---
title: "What exactly would you call 1/2 beryl?"
date: 2007-04-07
forum: Desktop Effects &amp; Customization
---

### Post by phoenixfirebird on 2007-04-07
I've tried almost all how-to's and suggestions I could find, but I can only get Beryl working about 50%.  That is, I have wobbly windows, transparency, Beryl as my default window manager, some scaling, and some of the new alt-tab chooser.   But that's about it.  No cube, nothing to do with showing all workspaces, no emerald themes.  Things have been getting better though, yesterday and update let me finally use all of the correct icon themes (which made the desktop look a whole lot nicer) and today I was finally able to switch themes from system, since I am still stuck with metalicy, to get away from that ugly blue stuff.

I am on an Acer Aspire 3100
ATI X1100
Ubuntu Feisty

I followed the guide on how to set up a XGL session, and downloaded Beryl.  I have most of the classic problems, no direct rendering in XGL, all that.  But nothing else has helped me at least get the cube.  All the settings in the beryl setting manager seem to be fine, but even with it activated in the manager, nothing works.  ctrl+alt+right/left switches desktops like normal, and ctrl+alt+mouse one just acts as if I was trying to do a box selection on the desktop. 

Can anyone help?

Edit:  Under System>Preferences>Sessions>Current Session There is something called compiz.real --no fbo --ignore-desktop-hints --sm-client-id default0 gconf gconf
there is nothing about Beryl, is this ok?

---

### Post by phoenixfirebird on 2007-04-08
Update:  I don't know what I did, but I had it working for a short time last night.  Then it stopped again...damn](*,) 

What am I doing wrong here?:confused:

---

### Post by phoenixfirebird on 2007-04-08
Ok, I've figured out that I'm actually not running beryl at all, its just the compiz part of desktop effects, which is why the emerald theme doesn't work and all the settings in beryl setting manager don't have any impact.  So, my question is, I am in a XGL session, I have beryl installed, how can I activate it?  Typing in beryl-xgl gets me no where.  Typing beryl gets me:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
 
and beryl-manager gets me:

** (beryl-manager:18747): CRITICAL **: can't execute beryl-xgl: Success

over and over.  What can I do?  Where can I get the GLX_EXT_tecture... and GLX_SGIX_fbconfig?  They both show up in glxinfo under server glx extensions.

---

### Post by dacool25 on 2007-04-16
bump 

i'm also having this problem.  Has anyone ever seen it or know how to fix it?

---

### Post by eentonig on 2007-04-16
Disable the Ubuntu desktop effects.

start bery by 

> 
beryl &
beryl-manager &

(Actually, I think only beryl-manager is needed. But since I'm not behind myown  pc, I'm not sure). Play with the settings in the beryl-manager

---

### Post by ronocdh on 2007-04-21
> **eentonig said:**
> Disable the Ubuntu desktop effects.

start bery by 



(Actually, I think only beryl-manager is needed. But since I'm not behind myown  pc, I'm not sure). Play with the settings in the beryl-manager
This did not work for me. Every time I start up beryl-manager, I get
```
** (beryl-manager:3813): CRITICAL **: can't execute beryl-xgl: Success

** (beryl-manager:3813): CRITICAL **: can't execute beryl-xgl: Success

** (beryl-manager:3813): CRITICAL **: can't execute beryl-xgl: Success
```
That repeats ad infinitum, keeping my processor (C2D 2.16GHz) at about 30% the whole time beryl-manager is running. If I quit it, processor calms down (and entries in the terminal cease).

Ideas?

---

### Post by GeDaMo on 2007-04-21
In a terminal, type ```
glxinfo | grep direct
```
What do you get?

---

### Post by fain on 2007-04-22
i have this same problem with a nvidia 7600GT sli when i type 

glxinfo | grep direct


i get


direct rendering: No

---

### Post by fain on 2007-04-23
ok this seems to be a temporary fix i found here
[http://forum.beryl-project.org/viewtopic.php?f=36&t=3756](http://forum.beryl-project.org/viewtopic.php?f=36&t=3756)
```
beryl-manager --no-force-window-manager
```
```
beryl-xgl --use-copy
```
i had to minus the xgl to get it working on the feisty repo packages
```
beryl --use-copy
```
seems to be working good now

---

