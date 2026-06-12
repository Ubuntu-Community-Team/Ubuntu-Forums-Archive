---
title: "GTK themes not showing"
date: 2018-05-28
forum: Desktop Environments
---

### Post by Drone4four on 2018-05-28
Some GTK3 themes that I've attempted installing for Gnome 3.28 are not available in Tweaks.

For example, have a look at [Telinkrin-GTK]("https://github.com/paullinuxthemer/Telinkrin-GTK").  I cloned the repo into ~/.themes.  Here are the contents of my .themes directory:

```
$ ls
Arrongin-GTK                     VimixDark
copernico-theme                  VimixDark-Beryl
Flat-Remix                       VimixDark-Beryl-dsw
Flat-Remix-dark                  VimixDark-Doder
Flat-Remix-dark-miami            VimixDark-Laptop
flat-remix-gnome                 VimixDark-Laptop-Beryl
Flat-Remix-miami                 VimixDark-Laptop-Doder
Gnome-OSC-Traditional--2-themes  VimixDark-Laptop-Ruby
Human-shell-theme                VimixDark-Ruby
Pro-Dark-GTK                     VimixLight
Sierra-compact-dark              VimixLight-Beryl
Sierra-compact-dark-solid        VimixLight-Doder
Sierra-compact-light             VimixLight-Laptop
Sierra-compact-light-solid       VimixLight-Laptop-Beryl
Sierra-dark                      VimixLight-Laptop-Doder
Sierra-dark-solid                VimixLight-Laptop-Ruby
Sierra-light                     VimixLight-Ruby
Sierra-light-solid               X-Arc-Darker
Telinkrin-GTK                    X-Arc-Plus
U8                               X-Arc-Shadow
U8SUB                            X-Arc-White
Unity8
$
```
There it is below Sierra-light-solid yet Telinkrin is nowhere to be found inside Tweaks. See attached. I also placed Telinkrin-GTK into /usr/share/themes. Still not showing. I restarted my Gnome shell session multiple times.

The instructions for installation on the maintainer's GitHub page are straightforward. I tried searching Google and these forums to see if other Ubuntu 18.04 users were affected.  Nothing.

The 4 X-Arc themes, along with Arrongin-GTK, aren't showing in Tweaks either.  I understand that X-Arc is deprecated and do not support 3.28 but Arrongin-GTK should surely be present in Tweaks.  

Any ideas?

Thanks for your attention.

---

### Post by Drone4four on 2018-05-28
Here are the contents of the Telinkrin-GTK directory: ```
$ ls -la
total 48
drwxr-xr-x  6 gnull gnull  4096 May 28 21:36 .
drwxr-xr-x 45 gnull gnull  4096 May 28 21:37 ..
-rw-r--r--  1 gnull gnull 18092 May 28 21:36 COPYING
drwxr-xr-x  8 gnull gnull  4096 May 28 22:28 .git
drwxr-xr-x  3 gnull gnull  4096 May 28 21:36 gnome-shell
drwxr-xr-x  4 gnull gnull  4096 May 28 21:36 gtk-2.0
drwxr-xr-x  3 gnull gnull  4096 May 28 21:36 gtk-3.0
-rw-r--r--  1 gnull gnull  2433 May 28 21:36 README.md
```
I noticed there is no `index.theme` file like there is in some of the other theme folders. Could this be Telinkrin-GTK? Or is this file more for gtk-2.0 theme elements?

---

### Post by again? on 2018-05-28
I cloned the git repo into ~/.themes and Tweaks shows both gtk and shell themes.
```
**[COLOR="#006400"]glen@Gubu:~$[/COLOR] ls -al ~/.themes/Telinkrin-GTK**
total 48
drwxr-xr-x 6 glen glen  4096 May 29 11:30 .
drwxr-xr-x 3 glen glen  4096 May 29 11:30 ..
-rw-r--r-- 1 glen glen 18092 May 29 11:30 COPYING
drwxr-xr-x 8 glen glen  4096 May 29 11:30 .git
drwxr-xr-x 3 glen glen  4096 May 29 11:30 gnome-shell
drwxr-xr-x 4 glen glen  4096 May 29 11:30 gtk-2.0
drwxr-xr-x 3 glen glen  4096 May 29 11:30 gtk-3.0
-rw-r--r-- 1 glen glen  2433 May 29 11:30 README.md

**[COLOR="#006400"]glen@Gubu:~$[/COLOR] du -hs  ~/.themes/Telinkrin-GTK** 
2.9M	/home/glen/.themes/Telinkrin-GTK

```

---

### Post by Frogs Hair on 2018-05-29
I installed  Telinkrin-GTK manually in usr/share/themes and it seems to work fine. Be sure when using manual installation that the themes are fully extracted from the master folder or they won't appear in the tweak tool.

---

