---
title: "GDM is messing up my fonts"
date: 2007-04-13
forum: Desktop Environments
---

### Post by navilon on 2007-04-13
I am using beryl alone as my window manager (not using GNOME or KDE) however I am using GDM for my login manager.

When i log in through GDM my fonts look like this..
[IMG]http://img464.imageshack.us/img464/6019/gdmscreenrk9.png[/IMG]

however, normally when I login thru the console using startx it looks normal..
[IMG]http://img362.imageshack.us/img362/6562/normalscreenvd3.png[/IMG]

Anyone have some ideas on why this is happening?

---

### Post by hackerssidekick on 2007-04-13
Looks like gnome may be changing the font/dpi settings.

In a terminal, do this:
```
xdpyinfo | grep dots
```
It will print out something like this:
```
  resolution:    99x98 dots per inch
```

Now open up the gnome font settings (gnome-font-properties in the terminal) and click on details. Change the value of **Resolution** to be the first number output above (so mine would be 99, because the output was 99x98).

Click close, and then in the Font Preferences window change the fonts to suit.

---

### Post by navilon on 2007-04-13
I dont use gnome so i dont have gnome-font-properties.
i tried 
```
sudo aptitude install gnome-font-properties
```
and it cant find it

can i change the DPI manually?

---

### Post by hackerssidekick on 2007-04-15
When you're logging in through gdm, which session do you log in to? It maybe that something else is changing the fonts upon login, since this doesn't happen when you startx.

Also, do you have a .xsession or a .xinitrc in your home folder? If so, post it here.

---

### Post by navilon on 2007-04-15
I've fixed the problem locally, but the fonts on the login screen are still pretty bad.

I added the following to my .Xdefaults file to fix the fonts after i logged in:
```
Xft.dpi: 96.0
```

is there a global Xdefaults file that i could do the same to?

---

### Post by hackerssidekick on 2007-04-15
You can set it in your /etc/X11/xorg.conf. There are some instructions here: [http://wiki.archlinux.org/index.php/Xorg7#Display_Size.2FDPI](http://wiki.archlinux.org/index.php/Xorg7#Display_Size.2FDPI)

There is some more information here: [http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts](http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts)

Note that both of those links are for other distributions, but the basic Xorg stuff will be the same.

---

