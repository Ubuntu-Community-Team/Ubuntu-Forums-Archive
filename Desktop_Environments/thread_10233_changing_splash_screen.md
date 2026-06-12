---
title: "changing splash screen"
date: 2005-01-06
forum: Desktop Environments
---

### Post by tiiim on 2005-01-06
not an urgent matter but just for reference how do i change the splash screen?

---

### Post by fng on 2005-01-06
Wait for hoary.
It will include usplash.

---

### Post by jbh on 2005-01-06
i have hoary 64, no sign of usplash. future release?

---

### Post by fng on 2005-01-06
[http://www.ubuntulinux.org/wiki/HoaryHedgehog](http://www.ubuntulinux.org/wiki/HoaryHedgehog)

Read at the end of the page.

---

### Post by Shaggy on 2005-01-07
WAIT FOR NUTTIN.

All you have to do is download whatever splash you want, it's usualy a PNG file.

```
sudu cp <splash name> /usr/share/pixmaps/splash/
``` 

Then in Nautilus
 
Apps->Gnome-Session->Option

You should see a key called "splash_image" whose value is "splash/ubuntu-splash.png"

Change the name of ubuntu-splash to whatever the name of your new splash is, will look like "splash/<splash name>" and you're good to go.

Pft wait for the next version.  This is linux there is always a way. :mrgreen:

Hmm should I put this in the howto section until the next release comes out?

---

### Post by Randabis on 2005-01-07
[QUOTE=Shaggy]WAIT FOR NUTTIN.

All you have to do is download whatever splash you want, it's usualy a PNG file.

```
sudu cp <splash name> /usr/share/pixmaps/splash/
``` 

Then in Nautilus
 
Apps->Gnome-Session->Option

You should see a key called "splash_image" whose value is "splash/ubuntu-splash.png"

Change the name of ubuntu-splash to whatever the name of your new splash is, will look like "splash/<splash name>" and you're good to go.

Pft wait for the next version.  This is linux there is always a way. :mrgreen:

Hmm should I put this in the howto section until the next release comes out?[/QUOTE]
 good tip, but I think he's talking about bootsplash, not the gnome splash

---

### Post by Shaggy on 2005-01-07
Oh 8-[ 

I hated it when my bubble is burst

---

### Post by labbe on 2005-01-08
> How do I change the GNOME splash screen?

To change the splash screen, put the downloaded image in an unobtrusive location (since it will need to remain there as long as you want it to be the splash screen). A logical location would be ~/.gnome/splash.png (or .jpeg if the image is a JPEG). Then, edit the GConf key /apps/gnome-session/options/splash_screen using the Configuration Editor (Panel menu->System Tools->Configuration Editor) or the commandline tool gconftool-2. 
This works!

---

### Post by tiiim on 2005-01-08
[QUOTE=labbe]This works![/QUOTE]
 cheers i forgot i was in Linux and you dont need a but option with colours to do things... hehe thanks that keep me happy now. :)

---

### Post by wallijonn on 2005-01-08
Just to clean up the instructions a little:

Root Terminal sudo copy your new splash image to /usr/share/pixmaps/splash
Applications -> System Tools -> Configuration Editor ->
/apps/gnome-session/options/show_splash_screen
Select splash image, Edit Key, select new splash image, OK, close / exit

I did it the lazy way, I [COLOR=Red]mv /usr/share/pixmaps/splash/ubuntu-splash.png /usr/share/pixmaps/splash/ubuntu-splash-old.png[/COLOR], then [COLOR=Red]sudo cp /home/[/COLOR]<usrname>[COLOR=Red]/xxx.png /usr/share/pixmaps/splash/ubuntu-splash.png[/COLOR]

---

### Post by Randabis on 2005-01-18
Another option is to use gTweakUI. Not sure if it is in warty, but it is in hoary. 
You can change it in gTweakUI - Session.

---

