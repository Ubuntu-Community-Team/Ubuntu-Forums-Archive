---
title: "Install Unity desktop without ubuntu applications?"
date: 2012-09-27
forum: Desktop Environments
---

### Post by bennypr0fane on 2012-09-27
Hello,
- I am trying to install the Untiy desktop on top of my Bodhi Linux (64 bit). It's an Ubuntu-based distro (12.04) that comes with only a bare minimum of applications and the Enlightenment desktop. I like the fact that I get to choose which the applications I actually need so nothing superfluous is installed.
However I would like to replace Enlightenment with the Unity desktop and have tried that by running
```
apt-get install ubuntu-desktop
```
that pulled the complete set of Ubuntu applications though,
so I believe what I have now is much the same as a regular installation of Ubuntu.
Is there a way to get *just the desktop*, without transforming my Linux completely into Ubuntu?

- Also, the result of what I did  (installing ubuntu-desktop on top of Bodhi Linux) is broken. When I log into an Ubuntu session, only the bare wallpaper is loaded, nothing to click appears, no icons, no taskbars or menus, nothing. On right-click, I get the context menu, and keyboard entries are acknowledeged in a small text box in the bottom right. Other than then that, a blank wallpaper.
looking into htop task manager in tty, there were no Unity processes running.
There were, I think, two Compiz processes.
I tried
```
apt-get purge ubuntu-desktop
```
which apparently removed only the one package, leaving all the others untouched. Then
```
apt-get autoclean && apt-get autoremove
```
removed only a couple other packages.
Reinstalling ubuntu-desktop after that gave the same result.

---

### Post by jerrrys on 2012-09-27
I don't know why you would want to do this, but ..

First take a look at [ubuntu-desktop package list]("http://packages.ubuntu.com/precise/ubuntu-desktop") .  You might as well forget bodhi and just install ubuntu.

Maybe you can just install [Unity]("http://packages.ubuntu.com/precise/unity") or just [Unity 2d]("http://packages.ubuntu.com/precise/unity-2d") .  I haven't tried this of course, so this is just guess work.

If you want to build your own, why no just use the [ubuntu mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") , its great for that.

good luck

---

