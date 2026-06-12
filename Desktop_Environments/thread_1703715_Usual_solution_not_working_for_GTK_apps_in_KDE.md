---
title: "Usual solution not working for GTK apps in KDE"
date: 2011-03-09
forum: Desktop Environments
---

### Post by gladiool on 2011-03-09
I was forced (by an unrelated problem) to reinstall my Kubuntu 10.10 from scratch today, and now I'm having a very annoying problem with the look of GTK apps in KDE.

I know I have to install gtk2-engines-qtcurve to make them blend in, and I know I need to copy some gtkrc files to /root to make it work for apps needing root privileges (e.g. Synaptic).

This has done the job for 80%, but they still don't look the way I they used to in my previous installation (which was Kubuntu 10.10 as well). As you can see in the two attachments, in applications run as a normal user the menu bar is lighter than it should be, and in applications run as root the entire window is this light.

I remember this was a problem the last time as well, but in the end I managed to fix it. The problem is: I have absolutely NO idea what the solution was back then, and even after several hours of googling, I have had no luck in finding it again.

Does anyone know the solution to this? Any help will be greatly appreciated!

---

### Post by ankspo71 on 2011-03-09
Hi,
This type of theme problem can happen because is there is no .gtkrc-2.0 file in our home folder (and root's home folder) for GTK applications to read settings from. Luckily there is a .gtkrc-2.0-kde4 file to copy these settings off of.

I fixed mine creating symbolic links (shortcuts) pointing to the gtkrc-2.0-kde4 file:
```
ln -s ~/.gtkrc-2.0-kde4 ~/.gtkrc-2.0
sudo ln -s ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0
sudo ln -s ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0-kde4
```

Paste each command one at a time in your terminal and press enter. Note: don't use sudo for the first command because we don't want to have a gtkrc-2.0 file owned by root in our home folder. 

By the way, if you like using the Oxygen theme for your applications, there is new Oxygen theme engine for GTK applications called Oxygen-GTK at kde-look.org. [http://kde-look.org/content/show.php/Oxygen+Gtk?content=136216](http://kde-look.org/content/show.php/Oxygen+Gtk?content=136216) . The author has also provided a deb package for easy installation. 

Also, remember to go to System Settings > Application Appearance > GTK+ Appearance > and choose your preferred widget style for GTK applications to use.

Hope this helps.

---

### Post by gladiool on 2011-03-10
Hi ankspo71,

Thanks for your help, but the problem is: I already did that. Before doing so, everything looked even uglier than it does now, but as you can see in the screenshots it still doesn't look the way it should.

And since I found a solution before, I know it's possible to fix it completely. The last time I remember also creating a symlink from the root folder to some file in ~/.kde, but I don't know what file that was and whether that turned out to be the final solution.

Any idea what that could have been?

---

### Post by schnelle on 2011-03-10
Try with gtk-chtheme. Run it, choose qtcurve and hit apply. 

Then run it with kdesudo, choose qtcurve and hit apply.

This helped me.

Cheers.

---

### Post by ankspo71 on 2011-03-10
> **gladiool said:**
> Any idea what that could have been?

I haven't tried what the above poster has mentioned so that may help. I'll go try it out myself because I'm curious at what it does.

The only other thing I can think of that you might have done before, is upgrade to the latest version of qtcurve.

I use Qtcurve too, but I use it for both my KDE and GTK applications. I've noticed that using Qtcurve in Maverick seems to be a little buggy. When I go to import and apply qtcurve themes, the theme's styles and colors  schemes don't get applied correctly. Upgrading qtcurve has helped these issues to an extent, but it has helped. So maybe upgrading qtcurve will help.

The following PPA repository has gtk2-engines-qtcurve 1.8.6.
[https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa) 
You can either add the repository and perform an upgrade, or you can download and install individual packages from this link:
[https://launchpad.net/~samrog131/+archive/ppa/+packages](https://launchpad.net/~samrog131/+archive/ppa/+packages)

Qtcurve can also be compiled from source code by downloading it from here:
[http://kde-look.org/content/show.php/QtCurve+%28KDE4%2C+KDE3%2C+%26+Gtk2+Theme%29?content=40492](http://kde-look.org/content/show.php/QtCurve+%28KDE4%2C+KDE3%2C+%26+Gtk2+Theme%29?content=40492)

Hope this helps.

---

### Post by gladiool on 2011-03-10
Thanks for your help guys, I found the solution.

The reason that some colors in my user applications were too dark, was because of one simple option in my KDE system settings:
"Apply color scheme to non-KDE 4 applications"

I actually DID try disabling that option before, so I knew it existed, but somehow when I changed it, the look of my GTK apps was not updated so I thought it had no effect.

However, I now turned off this option, then used gtk-chtheme to switch to another theme and then switch back to QTCurve. This caused the UI to be reloaded, and then all of a sudden the option in system settings was taken into account and the colors were fixed.

So thanks for the gtk-chtheme tip, schnelle!

---

### Post by schnelle on 2011-03-10
Glad to help.

Cheers :)

---

