---
title: "[SOLVED] Compiling xemacs 21.5.28 on Ubuntu 7.10"
date: 2008-01-24
forum: Desktop Environments
---

### Post by Jared Oberhaus on 2008-01-24
With some effort I've managed to compile xemacs 21.5.28 from source downloaded from xemacs.org on my Ubuntu 7.10 desktop.

First, you should have development tools installed, such as gcc and headers.

By default xemacs is looking for termcap which is apparently deprecated; instead you should use libncurses. Install the dev package:

```
sudo apt-get install libncurses5-dev
```

You'll also need the X11 dev packages, or it will compile something that will only run in a terminal:

```
sudo apt-get install libx11-dev
sudo apt-get install libxt-dev
```

I like anti-aliased text; if you want that, you'll need to install libxft dev package, which will bring along all the other things like freetype:

```
sudo apt-get install libxft-dev
```

Finally, you must run configure telling it about ncurses and xft:
```
./configure --prefix=<prefixdir> --with-ncurses --with-xft
```

Now, whether or not the vanilla source xemacs 21.5.28 is better than the 21.4.20 you get from universe is a decision I leave up to you...

---

### Post by Jared Oberhaus on 2008-02-07
Someone asked me how to configure this xemacs build that I outlined. Sorry, all I did was build it, see what it looked like, didn't like a few things, and gave up. Instead I use the xemacs that is available via apt-get for Ubuntu. (I have other problems with the standard distribution Ubuntu xemacs, but that's another post). What you probably want to do is:

```
apt-get install xemacs21
```

---

### Post by XProgrammer on 2008-02-12
Thanks Jared Oberhaus.

I'm currently using xemacs-21.4.x ( comes from gusty packages). It has annoying problem in maximizing the xemacs which takes much longer time.

I decided to try xemacs-21.5.28. Your post really helped me. 

One more question, when i did everything as you mentioned, I'm getting very basic GUI which is not equivalent to what i got in xemacs-21.4. do i need enable any other options in configure ?.

---

### Post by xyblor on 2008-02-20
> **XProgrammer said:**
> 
[...] I'm currently using xemacs-21.4.x ( comes from gusty packages). It has annoying problem in maximizing the xemacs which takes much longer time. [...]


I have experienced this too and I was wondering if perhaps installing the the package called "xemacs21-gnome-mule" or "xemacs21-gnome-nomule" might help this.
*EDIT* I just installed xemacs21-gnome-mule, and it does indeed maximize properly now, but you have to run "xemacs21-gnome-mule"; "xemacs" still runs the non-gnome version.

---

### Post by perce on 2008-03-15
> **XProgrammer said:**
> Thanks Jared Oberhaus.

I'm currently using xemacs-21.4.x ( comes from gusty packages). It has annoying problem in maximizing the xemacs which takes much longer time.

I decided to try xemacs-21.5.28. Your post really helped me. 

One more question, when i did everything as you mentioned, I'm getting very basic GUI which is not equivalent to what i got in xemacs-21.4. do i need enable any other options in configure ?.

What I did was to install a package  libxaw7-dev, and configure XEmacs with the options:

--prefix=/opt/xemacs-21.5.28 --with-xft --with-ncurses --with-sound=none,native --with-x11 --with-site-lisp --with-database=berkdb --with-msw=no --with-dynamic --without-error-checking --with-file-coding --with-pdump --with-system-malloc --with-menubars=lucid --with-scrollbars=lucid --with-dialogs=athena --with-canna=no --with-wnn=no --with-xpm --with-jpeg --with-xim=xlib

I don't completely understand many of these options. What I understand is that they, among other things, enable antialiasing, build the GUI, and install XEmacs in the directory /opt/xemacs-21.5.28

After the installation I followed the instructions in [http://www.xemacs.org/Install/](http://www.xemacs.org/Install/) about the sumo tarball.

Unfortunately however x-symbols don't work well, so I'll probably stick to 21.4 :(

---

### Post by Caml_Craig on 2008-03-17
> **xyblor said:**
> I have experienced this too and I was wondering if perhaps installing the the package called "xemacs21-gnome-mule" or "xemacs21-gnome-nomule" might help this.
*EDIT* I just installed xemacs21-gnome-mule, and it does indeed maximize properly now, but you have to run "xemacs21-gnome-mule"; "xemacs" still runs the non-gnome version.

I realize its been a while since you posted this reply xyblor, but I thought I would add my two cents. I did a quick search for the package you referred to 'xemacs21-gnome-mule' and found [[COLOR="Blue"]this[/COLOR]]("http://packages.ubuntu.com/hardy/xemacs21-gnome-mule"), which is for xemacs using non-European characters (i.e. Japanese, Chinese, etc...).

I am running ubuntu 7.10 gutsy gibbon so ran:

```
sudo apt-get install xemacs21-gnome-nomule
```

I did this because I don't need support for Asian languages. 

[QUOTE=XProgrammer]I'm currently using xemacs-21.4.x ( comes from gusty packages). It has annoying problem in maximizing the xemacs which takes much longer time.[/QUOTE]

Note: after installing the xemacs21-gnome-nomule package I no longer get the problem when maximizing xemacs, which I why I went though this exercise. Also, it doesn't matter if I use 'xemacs21-gnome-nomule' or just 'xemacs' to run the program, both run with complete GUI support and without the annoying maximize problem.

Hope that helps others out there that may be having trouble.

---

