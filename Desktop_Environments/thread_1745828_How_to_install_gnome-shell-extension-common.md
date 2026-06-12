---
title: "How to install gnome-shell-extension-common?"
date: 2011-05-01
forum: Desktop Environments
---

### Post by Drew93 on 2011-05-01
I have installed gnome 3 but it doesn't install the shell extension...I wrote this text but nothing "git clone git://git.gnome.org/gnome-shell-extensions
cd gnome-shell-extensions
./autogen.sh --prefix=/usr && make && sudo make install"
How can install the extension?

---

### Post by dim_par on 2011-05-01
Same problem with me too. I have installed from PPA

---

### Post by Drew93 on 2011-05-01
So do I...I hope someone responds

---

### Post by cbowman57 on 2011-05-01
Click the link under my signature.  There are some debs I converted from the Fedora rpm there.

Be advised though, there was a shell update this morning that broke a couple of them & activated a couple others that weren't working, i.e. broke the activities extension & activated alternate status (power off)

---

### Post by Drew93 on 2011-05-01
It doesn't work -.- ...i have installed this pack..i have restarted the explorer but nothing :twisted: ohter advice?

---

### Post by cbowman57 on 2011-05-01
You might try adding this ppa, this is the gnome-shell I'm running.
Everything just worked for me, I started with a fresh installation of natty.  Did you upgrade from 10.10?

[https://launchpad.net/~ricotz/+archive/testing]("https://launchpad.net/~ricotz/+archive/testing")

> **Drew93 said:**
> It doesn't work -.- ...i have installed this pack..i have restarted the explorer but nothing :twisted: ohter advice?

---

### Post by Drew93 on 2011-05-01
I have upgrade from 11.04...I have installed the repository and i reinstalled the shell extions. Nothing!

---

### Post by 23dornot23d on 2011-05-01
I keep a link here with all that I do on Gnome Shell ..... [LINK]("https://sites.google.com/site/000menu/home/gnome---3") to my collection of customization links
 and the way I installed it on my different set ups


Its mainly for me for reference but if you wade through it you may find something you have not found before .....

I have quite a lot of it working now and the files given in the link above do change the theme
from yellow to selectable using the *Gnome tweak tool *.....


There are some links to the Themes in [COLOR=Red]**[Deviant art THEMES]("http://gnome-shell.deviantart.com/gallery/28081982")**[/COLOR] and [[COLOR=Red]**web UPD8**[/COLOR]]("http://www.webupd8.org/2011/04/introducing-gnome-tweak-tool-gui-to.html") too for the tweak tool ..... might see if I can dig them out [**[COLOR=Red]Old Themes webUPD8 [/COLOR]**]("http://www.webupd8.org/2010/02/5-amazing-gnome-shell-themes-and-how-to.html").....

[MUSINGS THEME SELECTOR]("http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html")

This seems to be the important bit where he extracts these to .....


Place the downloaded tarball in *$HOME/.local/share/gnome-shell/* and unpack it.
```

You can download the *themeselector* extension [here]("http://fpmurphy.com/public/themeselector-0.8.tar.gz").   It contains all five Half-Left themes shown above.  Place the downloaded tarball in *$HOME/.local/share/gnome-shell/* and unpack it.   A new directory *themeselector@fpmurphy.com* will be created under *$HOME/.local/share/gnome-shell/extensions* to contain the extension code.  A new directory called *themes* will be created under *$HOME/.local/share/gnome-shell/*, and under this directory a series of directories will be created, one per theme.   [LEFT][COLOR=#000000]
Read more: [http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html#ixzz1L9B6E16D](http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html#ixzz1L9B6E16D)
[/COLOR][/LEFT]


```
Then you end up with this ..... [MY SCREENSHOT]("http://img98.imageshack.us/img98/8920/screenshot5fd.png")

---

### Post by Drew93 on 2011-05-02
Thank you! I have risolved to install the shell extension common :D :D :D but now I can't install the themeselector...I have put the file in the correct director but it doesn't run

Solved.... I wrong the folder where I had to put themes.

I have left an ultimate problem (the ultimate)...the bar at the right of the desk is always visible, also i surf the internet, the file manager, ecc. It's too uncomfortable because for example internet can't be maximized at all...i have attacched a picture

---

### Post by cbowman57 on 2011-05-02
Just go into ~/.local/share/gnome-shell/extensions and remove the extension that has "dock" in the name, same applies to any extension you don't want to use.  There is probably a clean way to do it but just removing the extension from the folder works.

I just use awn for a launcher, I can put it where I want & set it to autohide.  Synapse is also very handy combined with gnome 3.

---

### Post by Drew93 on 2011-05-02
It works equally...why all problems at me? xd

---

### Post by cbowman57 on 2011-05-02
If I can find a way to select gnome shell by default I was going to use Remastersys to create a custom distro but so far I can't get past the gdm to test the installer.

I've tried Fedora, and have the Suse live Gnome 3 distro installed.  I can see no differences in features or functionality compared to the gnome shell I've installed on Natty.

---

### Post by 23dornot23d on 2011-05-02
Thats good to know that the two systems are running parallel in functionality
do you have links to the fedora rpm's that you used too ....

Would like to find some more information out and also keep up to date with
the developments there too ..... ty

> 
I was going to use Remastersys to create a custom distro but so far I can't get past the gdm to test the installer.
What happens with gdm ..... ?

Is it possible to use kdm ...... I always switch to kdm as I prefer the start menu for selecting the desktop environment 
that I want ..... also it does not seem to fail like gdm does to get my Nvidia Graphics set up properly.

Only used Remastersys once before myself   ....... and could not get it to work as I wanted ......

But will be willing to help try to sort it out ........

---

### Post by cbowman57 on 2011-05-02
Those Fedora .rpms appear to be moving targets, the links I have point to files that are no longer there.

Probably have to use the search feature on this link and try to find whatever version replaced them.

[http://fr2.rpmfind.net/linux/RPM/Fedora_Project.html]("http://fr2.rpmfind.net/linux/RPM/Fedora_Project.html")

---

### Post by cbowman57 on 2011-05-02
Link to the Fedora .rpms

[gnome-shell-extensions-common]("http://rpmfind.net/linux/RPM/fedora/updates/testing/15/x86_64/gnome-shell-extensions-common-3.0.1-1.f016b9git.fc15.noarch.html")

[gnome-shell-extension-user-themes]("http://rpmfind.net/linux/RPM/fedora/updates/testing/15/x86_64/gnome-shell-extensions-user-theme-3.0.1-1.f016b9git.fc15.noarch.html")

---

### Post by 23dornot23d on 2011-05-02
Cheers for the links ..... will bookmark and have a good look through them ..... thank you

---

### Post by kjano on 2011-05-02
```

sudo alien gnome-shell-extensions-user-theme-YOURVERSION.fc15.noarch.rpm --scripts

sudo dpkg -i gnome-shell-extensions-user-theme_3.0.YOURVERSION_all.deb

```

---

### Post by 23dornot23d on 2011-05-02
Cheers kjano .... have now added that in my links as another way to package and install for Debian / Ubuntu

Thank you ....

---

### Post by bmbaker on 2011-05-03
here's my current extension library from the looking glass :-)

---

