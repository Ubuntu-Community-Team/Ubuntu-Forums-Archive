---
title: "Whats the difference between 'gnome shell' and the real deal gnome?"
date: 2012-05-31
forum: Desktop Environments
---

### Post by youknowme on 2012-05-31
Hello everyone,
I recently had debian squeeze with gnome as my desktop. However, i had problems getting my wireless card to work under debian and decided to try installing a new driver from the testing debian wheezy distribution. When i did this a bunch of new files were downloaded - probably even a new kernel! I figured if it worked it didn't matter - but the problem was my system failed to boot altogether. I took the decision to install ubuntu - which i have now done.

I have the unity desktop and was looking to install gnome. I could see from others that ubuntu supports gnome 3 shell, but that seems to be alongside unity. Also it does not allow me to even move the top status bar around like in the 'real' pure gnome. I would appreciate it if any of you folk could explain the difference between the 'gnome shell' and real gnome as im interested in fundamental technical differences.

Is this gnome shell just a few gnome features (such a menu)? It does not seem to be the real deal. Is it possible to have a real gnome desktop which allows me to configure all of it - ie so i can move the status bar from the top and place it at the bottom or even at the side of my screen?

In the past I have tried ubuntu and installed gnome (and other programs) from 'unsupported' repositories. I have always then had problems so i don't trust downloading important operating system features from anywhere or anyone other than an approved / monitored / supported website. In other words, i dont want gnome from john doe's homebrew package repository as you never know what else you might be getting.

can i get the real gnome from a fully legitimate source?
Please can anyone help?

---

### Post by qamelian on 2012-05-31
Gnome-shell is 'the real deal'. It is the default graphical shell for Gnome 3 on machines with the graphical hardware to handle it. I believe the version of Gnome in Debian Squeeze is version 2.3X which is no longer developed by Gnome.

---

### Post by 0011235813 on 2012-05-31
Gnome-shell is the "real deal gnome". Gnome 3.x uses GTK+3 while Gnome 2.x uses GTK+2. 
As for obtaining, have you tried searching for "gnome" (WITHOUT THE QUOTES) in the software center? That should bring up Gnome 3.4 in the Precise repositories. I still have to upgrade my Oneiric install, so I can't help you if you run into dependency issues.

---

### Post by traditionalist on 2012-05-31
Gnome shell is what you want;

[https://live.gnome.org/GnomeShell](https://live.gnome.org/GnomeShell)

[http://www.gnome.org/getting-gnome/](http://www.gnome.org/getting-gnome/)

[http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/)

---

### Post by traditionalist on 2012-05-31
You can also get it from the Ubuntu Software centre;

[[IMG]http://img713.imageshack.us/img713/4102/selection001xc.th.png[/IMG]](http://img713.imageshack.us/i/selection001xc.png/)

if you don't have the centre installed;

```
sudo apt-get install software-center
```

---

### Post by raptir on 2012-06-08
Sorry to bring up an old thread, but I found this while searching for some gnome-shell info and wanted to comment.

Gnome-shell is the new interface for Gnome 3.x, and replaced gnome-panel used in 2.x. Gnome-shell does not have quite as much customization available as gnome-panel did. For example, you can't move the top bar to the bottom of the screen (by default at least, maybe there is some plugin to allow it now). If you've installed the gnome-shell package from the repositories (sudo apt-get install gnome-shell) then you have the "real deal" Gnome as it is today. If you want a little more customization, try installing gnome-tweak-tool from the repos.

From your initial post, it sounds like you're really looking for gnome-panel again. Debian Squeeze still uses a 2.x version of Gnome, so that would be what you're used to. You can still get that in Ubuntu 12.04. Instead of installing gnome-shell, install the gnome-panel package. This will install the "fallback" mode for Gnome 3. If you log in to a "gnome fallback" session, you will get something that is pretty similar to gnome 2.x with compiz enabled. "Gnome Fallback (No effects)" will give you Metacity as your window manager. It still won't look quite like Gnome 2.x, because as others have mentioned it still uses Gtk3.

If that's all too long to read, gnome-shell (which it sounds like you have installed) is the new version of Gnome. Gnome-panel is also available, and would be more similar to what you're used to.

Edit: The login option for gnome-panel may be called Gnome Classic, not Fallback. I don't quite remember.

---

### Post by traditionalist on 2012-06-08
> **raptir said:**
> 

<SNIP>
Edit: The login option for gnome-panel may be called Gnome Classic, not Fallback. I don't quite remember.

The login options are "GNOME Classic"  and "GNOME Classic (No effects)"

You can move the panels anywhere you like.

---

