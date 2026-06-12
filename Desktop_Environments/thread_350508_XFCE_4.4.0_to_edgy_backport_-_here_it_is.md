---
title: "XFCE 4.4.0 to edgy backport - here it is"
date: 2007-01-31
forum: Desktop Environments
---

### Post by Rommidze on 2007-01-31
Due to lack of the native, I manualy rebuilded [_xfce 4.4.0 packages for Ubuntu edgy_]("http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy") from Ubuntu fiesty reposiory. This is a good way to install xfce 4.4.0 to your edgy - later on whole system update to fiesty it will be easily rulled. This will not happen if you will install via official xfce.org installer.

---

### Post by ~Mi on 2007-01-31
Thanks, **Rommidze**!

I've been using your packages for a few hours now and have been pleased, one thing you may wish to look into though is the xfce4-xmms-plugin which is supposed to work with XMMS, Beep Media Player or Audacious, I use Audacious ( [http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads) has an official Edgy repo and Audacious will be in Universe for Feisty) and it said I didn't have a supported player installed so I installed XMMS to see if I could get in and tweak the settings to point to Audacious and it still said I didn't have a player :-(

Other then that everything has worked flawlessly thus far for me including Composite! And the new XArchiver version in your repo has LHA support, no more command-line to open these archives!! *tears of joy*

Thanks again for these packages!!!
~Mi

---

### Post by Ghil on 2007-01-31
dah, and I just finished compiling XFCE official. -_-' thanks anyway Rommidze, I'll use them on the next install :P

---

### Post by Rommidze on 2007-02-01
> **~Mi said:**
> I've been using your packages for a few hours now and have been pleased, one thing you may wish to look into though is the xfce4-xmms-plugin which is supposed to work with XMMS, Beep Media Player or Audacious, I use Audacious ( [http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads) has an official Edgy repo and Audacious will be in Universe for Feisty) and it said I didn't have a supported player installed so I installed XMMS to see if I could get in and tweak the settings to point to Audacious and it still said I didn't have a player :-(

Yes, it's also doesn't work for mine, neither with Beep Media Player, nor with Audacious. Only with XMMS. I suppose this can be a plugin issue. :(

---

### Post by BoMbS14 on 2007-02-01
thank you!

---

### Post by kerry_s on 2007-02-01
Works thanks!

For those that want to change the desktop filesystem,home,trash,removable on the desktop, just edit xfdesktoprc.>
sudo mousepad /etc/xdg/xfce4/desktop/xfdesktoprc

it's simple true or false settings, i didn't want my floppy on the desktop. :D

---

### Post by kerry_s on 2007-02-01
Hey any chance your doing a *.deb for "thunar-volman" so we can use the volume management?

---

### Post by Rommidze on 2007-02-01
> **kerry_s said:**
> Hey any chance your doing a *.deb for "thunar-volman" so we can use the volume management?

Ok, I'll take a look for it. If it is already in fiesty repository, I'll rebuild it for sure. If not, it depends on how much to do.

---

### Post by kerry_s on 2007-02-01
> **Rommidze said:**
> Ok, I'll take a look for it. If it is already in fiesty repository, I'll rebuild it for sure. If not, it depends on how much to do.

Thank you very much! Your the best! :D

---

### Post by Rommidze on 2007-02-02
> **Rommidze said:**
> Due to lack of the native, I manualy rebuilded [_xfce 4.4.0 packages for Ubuntu edgy_]("http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy") from Ubuntu fiesty reposiory. This is a good way to install xfce 4.4.0 to your edgy - later on whole system update to fiesty it will be easily rulled. This will not happen if you will install via official xfce.org installer.

Because of the good amount of downloads, I have moved repository from Russian to the US server. Please refer to my blog post for instructions.

---

### Post by kerry_s on 2007-02-04
Does any body else have problems with the new mousepad going zombie every time it's used? 

I just found i had like 25 zombie mousepads running, I been so busy i didn't even spot it in my conky.

For now i just uninstalled mousepad and installed leafpad, which is what mousepad is based on. The only thing you lose is that running as root across the top.

---

### Post by Rommidze on 2007-02-08
> **kerry_s said:**
> Does any body else have problems with the new mousepad going zombie every time it's used?

I sometimes get Xfmedia as a zombie, but only when it hangs on some video samples.

---

### Post by picpak on 2007-02-14
With these repos, xfce4-mixer is broken. I can no longer add the xfce4-mixer-plugin to my panel.

---

### Post by picpak on 2007-02-14
Nevermind, it's not the packages. Something had messed up my soundcard. All is well now.

---

### Post by theadventuresofanidealist on 2007-02-14
after intallation my terminal makes the xfce desktop restart.
how can i fix this? can i uninstall xfce 4.40?how?

---

### Post by Rommidze on 2007-02-16
> **theadventuresofanidealist said:**
> after intallation my terminal makes the xfce desktop restart. how can i fix this? can i uninstall xfce 4.40?how?

Just to let everyone know. The reinstall of xfce4-terminal package solved the problem.

___________________________________
My case with [ati black screen on asus w3v]("http://tech.tolero.org/blog/en/linux/bad-proprietary-drivers").

---

### Post by Wangsta on 2007-02-21
hey, I just downloaded XFce 4.4.0 like it said, but I'm not getting what is promised. There's no compositing with the windows manager, and frankly, I can hardly tell the difference. How do I get transparency and the stuff promised in the Xfce 4.4.0 tour??

---

### Post by el_itur on 2007-02-23
I have a problem with xfwm4. The first time I've loged in it dind't run, I have to run it from lunks dialog and is working fine. but still I can't get to manage it's configuration. The settings manager tells me this when I click on windows manager settings or windows manager.
"Esta configuración no puede funcionar con su gestor de ventanas actual (unknown)"

translated it says :
"This configuration can't work with your windows managar (unknown)"


Any clue about this?

---

