---
title: "[SOLVED] What about if i dont want XGL to load all the time."
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by dgrafix on 2007-10-19
I followed this: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

And it worked fine, i now have compiz working. Problem is, its now using XGL in both sessions.

I want to be able to have a separate session for XGL. Weird thing is, it doesnt seem to matter weather i log in as gnome-xgl or as gnome it is the same when i type glxinfo.

However, 

if i apt-get remove xserver-xgl it defaults back to my direct rendering mode where i have fast OpenGL direct 3D.

How can i stop GLX loading from my default gnome session and only in the gnome-xgl one?

---

### Post by superyounan1 on 2007-10-19
are you using fglrx drivers?

---

### Post by toupeiro on 2007-10-19
I ran into the same scenario.  I was trying to help someone in #ubuntu with running Quake Wars if you have Xgl installed.  The only way I could do it is load a failsafe session.  So, I tried going through the steps I took to setup Xgl in 7.04 in the /usr/share/xsessions particularly, and I noticed that my gnome.desktop file does not have anything loading Xgl (yet, I am using it!).  So, how *do* you selectively load xgl in 7.10?  how is it loading xgl in the first place?

---

### Post by dgrafix on 2007-10-19
> how is it loading xgl in the first place? Exactly what i wanna know ! :)

Yes i am using the fglrx ati drivers

The only suitable way i have found to switch so far is:

To turn on compiz:
sudo apt-get install xserver-xgl
(restart xserver)

To turn off compiz:
sudo apt-get remove xserver-xgl
(restart xserver)

Which is fine by me, except i have to be connected to the net to switch it on!!

Surely theres an easier way :/

---

### Post by toupeiro on 2007-10-19
I was able to get around it by loading a gnome failsafe session. You can do that as opposed to uninstalling and reinstalling xgl, but that should be by no means the permanent solution.

---

### Post by dgrafix on 2007-10-19
Ive just figured it out. (thanks to an odd but timely info popup)

> mkdir ~/.config/xserver-xgl

then make an empty file in this folder simply called "disable":

> gedit ~/.config/xserver-xgl/disable    (then save)

Then follow that sessions guide i started the tread with (if you have not done so already) and it seems to be fixed :)

if i want** xgl with compiz** i start "gnome - xgl" session from the login screen
if i want **no xgl and true 3d accel **for games and blender etc, i start normal "gnome" session from the login screen

---

### Post by toupeiro on 2007-10-19
Awesome!  I'm going to try this now.  Great find!  Thank you!

---

