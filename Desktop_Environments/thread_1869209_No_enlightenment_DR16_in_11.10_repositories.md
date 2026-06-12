---
title: "No enlightenment DR16 in 11.10 repositories"
date: 2011-10-25
forum: Desktop Environments
---

### Post by nuclearaelcun on 2011-10-25
Binary packages for enlightenment DR16 seem to be missing.

Isn't anyone else victim to the timeless awesomeness of BlueSteel? ;)

---

### Post by Frogs Hair on 2011-10-25
I tried E17 on 11.10 and the core packages work , but the Gnome applications look awful .

With Gnome 2 it was possible to select appearance preferences and use the GTK 2 theme on the Gnome applications . This no longer works with Gnome 3 , so all Gnome applications appear with white administrative colors .

---

### Post by wlake on 2011-10-25
There is a nightly build ppa for e17 for oneiric on launchpad maintained by Hannes Janetzek. Check it out.

---

### Post by Frogs Hair on 2011-10-25
> **wlake said:**
> There is a nightly build ppa for e17 for oneiric on launchpad maintained by Hannes Janetzek. Check it out.

Thank you , I will try it out . There was a PPA for 11.04 , but I was not aware on this one .

---

### Post by nuclearaelcun on 2011-10-25
Hey,

I meant the DR16 release of enlightenment. The sources are available [here]("http://sourceforge.net/projects/enlightenment/files/"), and the binary packages used to be [there]("https://launchpad.net/ubuntu/natty/i386/e16/1.0.0-4ubuntu2") in Ubuntu 11.04. Debian packages are [available]("http://packages.debian.org/search?keywords=e16") too, it just seems to be missing from Ubuntu 11.10.

Somehow, over the past 7 years of Linux, I've always ended up coming back to e16! It kind of [looks nice]("http://www.erat.org/files/bluesteel/screenshot.jpg") :).

And to make Gnome things read some settings while running e17, you could either run gnome-settings-daemon, or you could patiently stitch together your .gtkrc files using gtk-chtheme and some Google. I'd recommend gnome-settings daemon, it does a lot more as is explained in this well-written [howto]("http://informatiq.org/content/using-e17-gnome3-session"). If you're really a ram miser, then it may pay to [figure out what's going on]("http://fluxbox-wiki.org/index.php?title=FAQ#Gtk2.2FGnome2_applications_look_weird_under_Fluxbox.2C_but_they_look_ok_when_gnome_is_started") and prepare an alternate .gtkrc file.

Hope this helps... And hope we get updated e16 packages soon!

---

### Post by nuclearaelcun on 2011-10-25
> With Gnome 2 it was possible to select appearance preferences and use  the GTK 2 theme on the Gnome applications . This no longer works with  Gnome 3 , so all Gnome applications appear with white administrative  colors .

Hey, try this [https://wiki.archlinux.org/index.php/GNOME#GTK3_theme_via_settings.ini](https://wiki.archlinux.org/index.php/GNOME#GTK3_theme_via_settings.ini)

---

### Post by wlake on 2011-10-26
Hello,
E17, itself, now has the ability to set the gtk themes under Settings>>Settings Panel>>Look>>Applications. I have installed it on Lubuntu 11.10. It integrates really well there.

wlake

---

### Post by WitchCraft on 2011-10-26
This is how exactly:

```

sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
sudo apt-get update
sudo apt-get install e17

```Works perfectly.
If it remains black on the first login, just press CTRL + ALT + PRINT_SCREEN +K to restart X, then try to login again.

Finally, a usable desktop replacement for gnome3.
KDE is too slow, XFCE too limited.
e17 -> A slight but smooth learning-curve for the total novice, but all-in-all pretty close to perfect

---

### Post by wlake on 2011-10-27
Hello Witchcraft,

If you haven't already done so, you might want to install some of the emodules to enhance the desktop. I stayed away from the WLAN emodules because I wanted to keep using network-manager and I didn't want the e17 dm, entrance either kept lxdm. Here's a screen shot of my desktop on Lubunt 11.10.

---

### Post by Frogs Hair on 2011-10-27
> **wlake said:**
> Hello,
E17, itself, now has the ability to set the gtk themes under Settings>>Settings Panel>>Look>>Applications. I have installed it on Lubuntu 11.10. It integrates really well there.

wlake

Thanks , I may check that out .

The core packages in the repository don't allow the installation of edje E17 theme packages  but the SVN PPA will .

---

### Post by Frogs Hair on 2011-10-27
> **nuclearaelcun said:**
> Hey,

I meant the DR16 release of enlightenment. The sources are available [here]("http://sourceforge.net/projects/enlightenment/files/"), and the binary packages used to be [there]("https://launchpad.net/ubuntu/natty/i386/e16/1.0.0-4ubuntu2") in Ubuntu 11.04. Debian packages are [available]("http://packages.debian.org/search?keywords=e16") too, it just seems to be missing from Ubuntu 11.10.

Somehow, over the past 7 years of Linux, I've always ended up coming back to e16! It kind of [looks nice]("http://www.erat.org/files/bluesteel/screenshot.jpg") :).

And to make Gnome things read some settings while running e17, you could either run gnome-settings-daemon, or you could patiently stitch together your .gtkrc files using gtk-chtheme and some Google. I'd recommend gnome-settings daemon, it does a lot more as is explained in this well-written [howto]("http://informatiq.org/content/using-e17-gnome3-session"). If you're really a ram miser, then it may pay to [figure out what's going on]("http://fluxbox-wiki.org/index.php?title=FAQ#Gtk2.2FGnome2_applications_look_weird_under_Fluxbox.2C_but_they_look_ok_when_gnome_is_started") and prepare an alternate .gtkrc file.

Hope this helps... And hope we get updated e16 packages soon!

E16 was not in the Ubuntu repository when I first tried E on 11.04 , but E17 was . That is why I brought up E17 .

---

### Post by nuclearaelcun on 2011-10-27
Thanks for the E17 PPA! I was looking for an updated one... Still nothing on E16 eh?

---

### Post by phroggelator on 2011-10-31
No e16 in 11.10 - looks like debian has dropped support upstream:

[https://launchpad.net/ubuntu/oneiric/+source/e16/1.0.0-4ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/e16/1.0.0-4ubuntu2)

Which is really annoying as I prefer e16 over e17 since the virtual desktop in e16 lets you have windows straddling each virtual desktop segment - very handy when you need an 800 character wide terminal.

Unless of course someone knows how to get e17 to do this.....

---

### Post by wlake on 2011-10-31
@phroggelator

I don't think this is supported in E17. But here is a wide terminal for you (not what you want), however although I can type past the edge of the screen I have to use the mouse to drag the window over to see the extra width.

---

### Post by bcastalia on 2011-12-08
Well, nuts. I've just completed an upgrade to 11.10 (oneiric) after having been happily stable for a long time using e16. And now I find that's it's gone and can't be recovered:

```

> sudo apt-get install e16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package e16 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

Ouch!!

I tried the e17 installation, but it appears quite clunky compared to e16, and consistently crashes (segv) whenever the application menus are accessed which makes it useless.

I'm very eager to find a repository with e16 ....

Thnx.

---

### Post by Anagonda on 2011-12-29
Yeah, where is my E16?

Do I really need to compile it? Few years ago, okay, a bit more years, it was the only way to get enlightenment, but it was always worth it.

There is no way E17 can fix the hole that E16 leaves, too slow and too "cake decorated". And of course the normal use is not that smooth.

---

### Post by Frogs Hair on 2011-12-29
I don't think it has been in the repository since 10.04 or before(wrong)  . I found the E16 data package for up to 11.04 , but I don't know if the core packages were all available in the software center because I was using E17 . [http://pkgs.org/download/e16-data](http://pkgs.org/download/e16-data)

---

### Post by nuclearaelcun on 2012-06-01
Damn. E16 missing in 12.04. I need my BlueSteel.

---

