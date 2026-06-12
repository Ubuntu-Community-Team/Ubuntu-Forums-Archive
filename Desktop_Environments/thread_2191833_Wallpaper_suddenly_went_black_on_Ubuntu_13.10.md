---
title: "Wallpaper suddenly went black on Ubuntu 13.10"
date: 2013-12-04
forum: Desktop Environments
---

### Post by lads on 2013-12-04
This one is really strange. Two days ago the wallpaper on Ubuntu 13.10 simply went black. I have repeatedly tried to change it in the Appearance menu back to an image, or one of the default wallpapers, but it remains persistently black. I have no clue on what to do. Thanks.

Things I have tried that did not work:

[LIST]
[*]    *gsettings set org.gnome.settings-daemon.plugins.background active true*
[*]    Turning "Have file manager handle the desktop" off in the Gnome Tweak Tool;
[*]    Purging the gnome3 PPA;
[*]    Setting the wallpaper with Firefox;
[/LIST]

I have desktop icons, thus I don't think that could be a cause.

---

### Post by tulisqiya on 2013-12-04
Perhaps a piece of software inside your computer there is a problem

---

### Post by lads on 2013-12-05
> **tulisqiya said:**
> Perhaps a piece of software inside your computer there is a problem

Perhaps. The question is which.

---

### Post by Frogs Hair on 2013-12-05
Unity uses the dconf Editor and I don't remember if it is installed bay default in 12.04 . This is how the background setting appears in 13.10 and the  picture uri is displayed. The path to the setting is displayed on the bottom, but may differ on 13.10.

---

### Post by lads on 2013-12-07
Here are the settings at dconf. I don't see anything strange...

---

### Post by Frogs Hair on 2013-12-07
The settings look the same as mine . Make sure that Nautilus is set to handle desktop in the Gnome Tweak Tool . You haven't mentioned any PPA's ,but the Gnome 3.10 PPA has caused background display problems for some people.

---

### Post by lads on 2013-12-14
I captured [a video of this strange desktop behaviour]("http://www.youtube.com/watch?v=FTaDJOaupQI"). Any further hints on how to get this back to normal are welcome.

---

### Post by Frogs Hair on 2013-12-16
See  from post  three and after . I know you have tried the configuration editor and it is reported not to work with 13.10. Turning off desktop handling will shut off the desktop context menu and you wont be able to work with files on the desktop.    

[http://askubuntu.com/questions/287571/desktop-shows-a-white-or-black-background-instead-of-wallpapers](http://askubuntu.com/questions/287571/desktop-shows-a-white-or-black-background-instead-of-wallpapers)

---

### Post by lads on 2014-01-04
> **Frogs Hair said:**
> See  from post  three and after . 

I have now tried all the fixes suggested in the question (including deleting the desktop configurations) and none works on Ubuntu 13.10, possibly because the issue has different causes in this later release.

Any further hints are welcome.

---

### Post by Frogs Hair on 2014-01-04
I don't know of any. Some search results seem to indicate that the Gnome 3.10 ppa breaks Unity and to what degree varies. You might want to backup reinstall and stick with the repository version of the Gnome Shell.

---

### Post by lads on 2014-01-05
> **Frogs Hair said:**
> Some search results seem to indicate that the Gnome 3.10 ppa breaks Unity and to what degree varies.

I have Gnome 3.8.4, which I believe is the default version shipped with Ubuntu 13.10:

```
$ apt-cache show gnome-shell | grep Version 
Version: 3.8.4-0ubuntu5
```

I haven't change anything in Gnome, nor did I install any extra Gnome packages. I do not have any Gnome PPA registered.

```
$ cat /etc/apt/sources.list | grep gnome
$
```

---

### Post by Frogs Hair on 2014-01-05
The first post indicates that the GNOME 3 Team PPA was purged . I thought may be the source of the problem . When using it I was unable to remove all the packages and had to reinstall.

Open the Gnome Tweak Tool and under Desktop see if the Picture URI is correct or even visible. Browsing pictures is also possible from there. Gnome Tweak has been a bit flaky for some users on 13.10.

---

### Post by lads on 2014-01-05
> **Frogs Hair said:**
> Open the Gnome Tweak Tool and under Desktop see if the Picture URI is correct or even visible. Browsing pictures is also possible from there. Gnome Tweak has been a bit flaky for some users on 13.10.

Frog's Hair, thank you for the continued support on this. I do not see anything strange in the Tweak Tool; I'm attaching some screen-shots.

---

### Post by Frogs Hair on 2014-01-05
I know the theme you are using hasn't been updated for 3.8 yet , so try a 3.8 compatible theme log out and in. 

[http://www.noobslab.com/2013/07/salience-gtk-theme-for-ubuntu.html](http://www.noobslab.com/2013/07/salience-gtk-theme-for-ubuntu.html)

---

### Post by lads on 2014-01-06
> **Frogs Hair said:**
> I know the theme you are using hasn't been updated for 3.8 yet , so try a 3.8 compatible theme log out and in. 

I switched the theme back to Ambience and restarted. The wallpaper yields the same behaviour....

---

### Post by Swappiness on 2014-01-06
I have a similar problem with KDE except instead of a blank background every time I boot/reboot it reverts to the default background.

---

### Post by lads on 2014-01-07
I don't know how relevant this information may be: logging in with a Gnome Flashback session the wallpaper also yields the same strange behaviour.

---

### Post by lads on 2014-01-08
I found out that my problems are caused by Cinnamon. I never installed it myself, but I use Nemo. The [package catalogue]("http://packages.ubuntu.com/saucy/nemo") does not list any Cinnamon packages as dependencies for Nemo, but somehow it got fully installed. The solution to bring the wallpaper back to functioning order is thus:

```
sudo apt-get remove cinnamon*
sudo apt-get autoremove
```

And afterwards log out and log back in.

Weird thing is: this actually removed Nemo and now I don't have a graphical file manager.

---

### Post by Frogs Hair on 2014-01-08
You can install Nautilus if it is not . I tried Cinnamon, but don't remember the process removing Nautilus . See revert changes if you used the following method. [http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

---

### Post by lads on 2014-01-09
Thanks Frogs Hair. I installed Nemo from the webupd8team PPA and it works pretty well, even RabbitVCS is functional. 

IMHO Nautilus 3.8 is not a graphical file manager, it is just a toy.

---

### Post by ravimeetsu on 2014-02-06
> **Frogs Hair said:**
> The settings look the same as mine . Make sure that Nautilus is set to handle desktop in the Gnome Tweak Tool . You haven't mentioned any PPA's ,but the Gnome 3.10 PPA has caused background display problems for some people.

I had to install ```
gnome-tweak-tool
```. 

On the terminal: 

```
gnome-tweak-tool
``` and ```
Desktop -> Have file handler manage the desktop.
```

I have also attached a picture. Hope that helps.

---

