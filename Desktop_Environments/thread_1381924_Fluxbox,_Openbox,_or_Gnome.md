---
title: "Fluxbox, Openbox, or Gnome???"
date: 2010-01-15
forum: Desktop Environments
---

### Post by Barriehie on 2010-01-15
I've had it with the gnome-settings-daemon errors!  I've done a complete reinstall and it still appears, although not as much.  If I've got this right I can replace my gnome WM with either fluxbox or openbox and that error box will go away, right???  So, what are the pros and cons of fluxbox and openbox, or alternatives?  I'm leaning towards fluxbox, all input appreciated and thanks in advance people. :)

Barrie

Edit: See my post [[color="blue"]here[/color]](http://ubuntuforums.org/showthread.php?p=8669019#post8669019) regarding my current state of affairs.

---

### Post by mk1w86 on 2010-01-15
I'm not sure why you're having so many problems with Gnome but you could try XFCE.  To install it run:

```
sudo aptitude install xubuntu-desktop
```

---

### Post by cascade9 on 2010-01-15
> **mk1w86 said:**
> I'm not sure why you're having so many problems with Gnome but you could try XFCE.  To install it run:

```
sudo aptitude install xubuntu-desktop
```

+1. For a gnome user, its the obvious choice if your going to change your DE/WM

But I wouldnt install xubuntu, you might be better off just getting xfce and whatever xfce packages you want (personally, I like a lot of the xfce packages that xubuntu ignores, so I am biased)

---

### Post by Barriehie on 2010-01-15
> **mk1w86 said:**
> I'm not sure why you're having so many problems with Gnome but you could try XFCE.  To install it run:

```
sudo aptitude install xubuntu-desktop
```

I don't know either!  This box has been working really well since I nuked windows in March, '08.  So I'm going to guess that xubuntu perhaps might integrate better with the X system???  I'll have to check out how well it incorporates my current setup, although I've gotten quite adept at restoring at this point...

---

### Post by hariks0 on 2010-01-15
Why don't you try [Ultimate Edition 2.5]("http://sourceforge.net/projects/ultimateedition/files/") based on karmic with 3 DEs and almost everything preloaded? You can add other DEs on this easily using the Ultamatix in it.

---

### Post by 3Miro on 2010-01-15
I hold the position that right now the only stable DE for Ubuntu is XFCE. KDE is not yet fully compatible and Gnome is clumsy outdated. It has almost all features of Gnome (you can even run compiz, but I think that might defeat the main goal of XFCE to make a very fast DE). I am using XFCE as main DE on several machines and I had never used that until 2 months ago.

```
sudo apt-get install xfce4 xfce4-goodies
```

did the trick for me.

---

### Post by Barriehie on 2010-01-15
> **3Miro said:**
> I hold the position that right now the only stable DE for Ubuntu is XFCE. KDE is not yet fully compatible and Gnome is clumsy outdated. It has almost all features of Gnome (you can even run compiz, but I think that might defeat the main goal of XFCE to make a very fast DE). I am using XFCE as main DE on several machines and I had never used that until 2 months ago.

```
sudo apt-get install xfce4 xfce4-goodies
```

did the trick for me.

Compiz does nothing for me! metacity --replace and save the sesseion!  I see that fluxbox still runs under/behind/between GDM so installing that won't necessarily do anything, sort of lessen system load.  I've found [[color="blue"]this site[/color]](http://xwinman.org/) and thanks to your post am checking out xfce.  I so want to be done with *blah blah blah **error.***

---

### Post by Barriehie on 2010-01-15
So in an effort to make all this work I've installed:
```

xfce4
xfce4-artwork
xfce4-battery-plugin
xfce4-clipman-plugin
xfce4-cpufreq-plugin
xfce4-cpugraph-plugin
xfce4-diskperf-plugin
xfce4-fsguard-plugin
xfce4-genmon-plugin
xfce4-goodies
xfce4-icon-theme
xfce4-mailwatch-plugin
xfce4-mcs-manager
xfce4-mcs-plugins
xfce4-mcs-plugins-extra
xfce4-mount-plugin
xfce4-netload-plugin
xfce4-notes-plugin
xfce4-panel
xfce4-places-plugin
xfce4-quicklauncher-plugin
xfce4-screenshooter-plugin
xfce4-sensors-plugin
xfce4-session
xfce4-smartbookmark-plugin
xfce4-systemload-plugin
xfce4-taskmanager
xfce4-terminal
xfce4-utils
xfce4-verve-plugin
xfce4-wavelan-plugin
xfce4-weather-plugin

```
Might be a bit of overkill to check it out but right now it's using 25% less RAM and is faster AND the xfce version of the gnome-settings-daemon error has popped up... :(  At least xfce will let me try again.  So, what I'm missing really much right now is a panel and a clock.  Any help please!  Thank you!

---

### Post by Barriehie on 2010-01-15
Figured out the clock thing!

---

### Post by bcrowell on 2010-01-15
Fluxbox works great for me. I've also used xfce on older hardware and liked it very much. If you want something that feels like Gnome, xfce may be a better-performing alternative. Personally I've never liked the whole idea of having my screen littered with little icons for files, so fluxbox works fine for me. (I think you can also add an optional GUI file manager to fluxbox, but I haven't done it.)

If you experience long login times on karmic with wm's other than Gnome, this may be the reason: [http://ubuntuforums.org/showthread.php?t=1382348](http://ubuntuforums.org/showthread.php?t=1382348)

---

### Post by Rodney9 on 2010-01-16
I love Fluxbox for it's simplicity.

Don't miss Red Squirrel's terrific tutorial on customizing Fluxbox - [http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+icons](http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+icons)

---

### Post by Barriehie on 2010-01-16
> **Rodney9 said:**
> I love Fluxbox for it's simplicity.

Don't miss Red Squirrel's terrific tutorial on customizing Fluxbox - [http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+icons](http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+icons)

Installed last night; yet to configure!

---

### Post by Barriehie on 2010-01-16
> **Rodney9 said:**
> I love Fluxbox for it's simplicity.

Don't miss Red Squirrel's terrific tutorial on customizing Fluxbox - [http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+icons](http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+icons)

So how about a screenshot??? :)  I've got it up and running but as yet the screen dmensions are off, it's in 800x600 and not 1024x768 :(  but it is fast!

---

### Post by Locutus_of_Borg on 2010-01-16
i am obligated to promote openbox

use openbox!!!

---

### Post by Rodney9 on 2010-01-17
> **Barriehie said:**
> So how about a screenshot??? :)  I've got it up and running but as yet the screen dmensions are off, it's in 800x600 and not 1024x768 :(  but it is fast!

Fast , unbelievably fast, After the Ubuntu start screen I can't count to three and Fluxbox is up and running. 
I love its minimal style and simplicity in use and setup.

[IMG]http://farm3.static.flickr.com/2803/4280995540_12579888ec_b.jpg[/IMG]

---

### Post by Barriehie on 2010-01-17
Looks good rodney9, I've a bit to go... :)

---

### Post by stanca on 2010-01-17
Enjoy it Rodney!As I do.;):)

---

### Post by mkvnmtr on 2010-01-17
I have only flux box on one 9.10 installation and it is fine but I began to use LXDE on PCLinux and have now installed it on a 9,04 Gnome install. I think I like it better than any I have used. And it is indeed light.

---

### Post by tweaksource on 2010-01-22
> 
I see that fluxbox still runs under/behind/between GDM so installing that won't necessarily do anything, sort of lessen system load.


Fluxbox does not have any ties to or dependencies upon Gnome anything.

GDM is not needed (or recommended, IMHO).

---

### Post by Barriehie on 2010-01-22
> **tweaksource said:**
> Fluxbox does not have any ties to or dependencies upon Gnome anything.

GDM is not needed (or recommended, IMHO).

I'm liking it too!  The more I run this the less enthused I am about running a 'fat' window manager.  Less is more...

---

