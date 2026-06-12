---
title: "Transparency in fluxbox is black ??"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by Cows on 2007-05-26
Hello. When I try to put transparency in fluxbox my transparent window turns black instead of actually being transparent .. look:

[http://i6.photobucket.com/albums/y213/Nibbler26/Screenshot-3.png](http://i6.photobucket.com/albums/y213/Nibbler26/Screenshot-3.png)

How do I fix this .. It also happens when I try to put transparency in gnome-terminal profile.

---

### Post by Cows on 2007-05-26
Bump

---

### Post by RedSquirrel on 2007-05-26
Did you try restarting? fluxbox menu -> Restart

What program are you using to set the background?

```
 fbsetbg -i
```

should say something about "<program_name> is a nice wallpapersetter. You won't have any problems."

If not, then install feh:

```
 sudo apt-get install feh
```

---

### Post by Cows on 2007-05-26
```
jv@localhost:~$ fbsetbg -i

display doesn't set the wallpaper properly. Transparency for fluxbox and apps like aterm and xchat won't work right with it. Consider installing feh, wmsetbg (from windowmaker) or Esetroot (from Eterm) and I'll use them instead.

jv@localhost:~$ 

```

I guess thats my problem. Thanks :).

---

### Post by gustavocm on 2007-05-31
How do i set the menu transparency if in my fluxbox configure menu there is no 'transparency' submenu?

i set:
session.screen0.menu.apha: 100
in the ~/.fluxbox/init file, and restarted flubox. Nothing changed.

what i have to do?
thank you

---

### Post by RedSquirrel on 2007-05-31
> **gustavocm said:**
> How do i set the menu transparency if in my fluxbox configure menu there is no 'transparency' submenu?

i set:
session.screen0.menu.apha: 100
in the ~/.fluxbox/init file, and restarted flubox. Nothing changed.

what i have to do?
thank you

Have a look at this to see all the things you need to have transparency:

[http://fluxbox.sourceforge.net/docs/en/faq.php#transparent](http://fluxbox.sourceforge.net/docs/en/faq.php#transparent)

For example, what does 

```
fbsetbg -i 
```report on your system?

You should have an entry like this somewhere in your menu:

```
[config] (Configure) 
```How did you create the menu? I would advise you to use one of the tools to generate a menu. If you're using a version of Fluxbox that you compiled yourself, you should have fluxbox-generate_menu in /usr/local/bin.

If you're using the version from the repositories, fluxbox-generate_menu is provided as a gzip compressed file. See the menu HOWTO in my sig. Near the bottom of the HOWTO, there is a section on how to install fluxbox-generate_menu.

Note: before you run fluxbox-generate_menu, you might want to backup the file ~/.fluxbox/menu, since that will be overwritten by fluxbox-generate_menu when you run it.

---

### Post by gustavocm on 2007-05-31
it seems that my X is without the XRender (or maybe the fluxbox isn't recognizing it), when i type **fluxbox -i** appears a '-RENDER'
but when i enter **xdpyinfo | grep RENDER** there is a 'RENDER'

Do you know how i install the XRender (or how i make the fluxbox recognize it) ?

---

### Post by RedSquirrel on 2007-05-31
It looks like your Fluxbox was compiled without Xrender support. That means you'll have to compile it again. Xrender should be on by default in the configure script. You can check with 

```
./configure -h
```

The option is "--enable-xrender".

I'm fairly certain the Fluxbox in the repositories has Xrender built in.

---

### Post by gustavocm on 2007-06-02
there are other compiled options that are disable:

```
Compiled options (- => disabled): 
-DEBUG
EWMH
GNOME
-IMLIB2
KDE
-NLS
REMEMBER
-RENDER
SHAPE
SLIT
TOOLBAR
-XFT
-XINERAMA
-XMB
XPM

```

now that i will compile fluxbox again, is there any other options that i should enable, any other interesting option?

thank you

---

### Post by RedSquirrel on 2007-06-02
I tend to stick with the defaults, which are:

```
Compiled options (- => disabled): 
-DEBUG
EWMH
GNOME
-IMLIB2
KDE
-NLS
REMEMBER
RENDER
SHAPE
SLIT
TOOLBAR
XFT
-XINERAMA
XMB
XPM
```Sometimes I disable slit support since I don't use the slit very often, but I'm mostly content with default configure options.

---

### Post by BOBSONATOR on 2007-06-02
sudo apt-get install eterm

---

### Post by RedSquirrel on 2007-06-03
> **BOBSONATOR said:**
> sudo apt-get install eterm

Yes, eterm or feh will do nicely, but one still has to have Xrender support in their build of Fluxbox. I prefer feh because I use a plain xterm for a terminal. ;)

---

