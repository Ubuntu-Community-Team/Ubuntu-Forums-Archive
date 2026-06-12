---
title: "Cannot pass the login screen"
date: 2011-01-02
forum: Desktop Environments
---

### Post by preclik on 2011-01-02
Hi,

I have a problem with Kubuntu 10.10. I cannot pass the login screen. When I type the password and press enter, the screen blinks once and I'm back at the login screen. 
When I try console login, there's no problem at all, but when I type startX, it ends up with a black screen.
I wasn't configuring anything before the problem appeared, I think I just activated Kwallet.

I'm a linux noob, so I didn't really know where to look. Here are logs I found.
Sry for my bad english. 

Preclik


[http://dl.dropbox.com/u/6872027/auth.log](http://dl.dropbox.com/u/6872027/auth.log)
[http://dl.dropbox.com/u/6872027/Xorg.0.log](http://dl.dropbox.com/u/6872027/Xorg.0.log)
[http://dl.dropbox.com/u/6872027/user.log](http://dl.dropbox.com/u/6872027/user.log)

Edit: I looked into a user.log, it seems there's a problem with accessing file .esd.auth. I used chmod, so the file should be accessible to everyone, but problem persists.

---

### Post by Untitled_No4 on 2011-01-03
In the login window there is a button on the top left for choosing your session. Click on it and make sure KDE is selected.
Alternatively, you can try deleting the ~/.dmrc file (a new one will be automatically created).

Hopefully this will solve your issue.

---

### Post by preclik on 2011-01-03
Thank you for your advice,
unfortunately it didn't work.

Can you, or someone else tell me, where to look (which log files) to identify the problem?

---

### Post by Zorael on 2011-01-03
This might be startkde crashing. Does **/var/log/kdm.log** say anything of interest?

---

### Post by preclik on 2011-01-03
I says this:

[http://dl.dropbox.com/u/6872027/kdm.log](http://dl.dropbox.com/u/6872027/kdm.log)

Not really sure what does it mean.

---

### Post by Zorael on 2011-01-03
Is your root partition full? You could try clearing the apt cache.
```
$ sudo aptitude clean
```

Also in some of the startup attempts kdmgreet seems to throw an error about not finding the pixmap "" ...
```
kdmgreet(1293) KdmPixmap::loadPixmap: failed to load ""
```
Have you tinkered with login themes in some way?
```
$ **grep Theme /etc/kde4/kdm/kdmrc**
# overridden settings are: UseBackground, BackgroundCfg, UseTheme, Theme.
UseTheme=true
**[COLOR="RoyalBlue"]Theme=/usr/share/kde4/apps/kdm/themes/ethais[/COLOR]**
#AllowThemeDebug=true
```
The path in blue must point to a proper theme. The default **ethais** is part of the **kdm** package, and the wallpapers it uses are in **kdebase-workspace-wallpapers**.
```
$ sudo aptitude reinstall kdm kdebase-workspace-wallpapers
```
If there's anything wrong with the files themselves, that should reinstall them from repositories. You need a net connection for this, though. This won't touch configuration files, mind.

If this is what's causing it, you could also work around the issue by disabling theming completely.
```
$ sudo cp /etc/kde4/kdm/kdmrc /etc/kde4/kdm/kdmrc.backup
$ sudo sed -i 's/UseTheme=true/UseTheme=false/g' /etc/kde4/kdm/kdmrc
```

---

### Post by preclik on 2011-01-03
Thank you Zorael, I apprecaite your help.

Unfortunately it seems my problem is not related to anything you suggested.
I'm going to reinstall Kubuntu tomorrow, it's not a big deal.

I just don't get it, what the hell happened?

---

