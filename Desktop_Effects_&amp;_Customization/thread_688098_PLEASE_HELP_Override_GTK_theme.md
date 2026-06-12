---
title: "*PLEASE HELP* Override GTK theme"
date: 2008-02-05
forum: Desktop Effects &amp; Customization
---

### Post by Izza on 2008-02-05
Is there a way to override the GTK theme per-application? :confused:

Any help anyone could give would be most appreciated! Thanks!

---

### Post by fredbird67 on 2008-03-11
Not that I'm aware of.  In fact, I don't think ANY desktop environment or window manager aloows you to do that.  Not KDE, GNOME, Xfce, Fluxbox, IceWM, Openbox...can't be done, my friend.

---

### Post by zz9pluralzalpha on 2008-03-11
Actually, I believe it IS possible. Certainly, that's how gtk-theme-switch works. I was just reading that the old Motif widget set allowed per-application theming. This is, by the way, a widget-level problem, and nothing to do with desktop environment or window manager.

All that said, I've no idea how to do this with GTK. Possibly some mucking about with gtkrc files would work, but it might be very hacky. Good luck plodding through the docs on that one.

If you find out how to do it, let me know because I want to run a dark theme for all apps except browsers, which tend to work poorly with dark themes.

---

### Post by zz9pluralzalpha on 2008-03-13
OK, I did some research. Technically, it is possible - just try changing your theme and then running something as root. However, gnome currently doesn't provide an easy way to do this unless the application has specifically coded it in.

Basically, GTK gets it's theme from a gtkrc file. This is searched for in a number of locations such as ~/gtkc-2.0. Applications can add their own paths to this list, allowing theme overiding on a per-application basis. But I'm not aware of any apps that actually make use of this.

There is a further problem. Under gnome, apps get their theme from the gnome-settings-demon. This instantaneously applies any theme change to all active applications, making per-appplication theme changing impossible.

If you try a non-gnome app, such as mousepad, you can run it, change ~/gtkrc-2.0, and run it again, and have two copies of it running, each with a different theme. But even here, turning this into a practical system for per-application theming would be a pig.

In short, you'll just have to wait for gtk-3.0.

---

### Post by kerry_s on 2008-03-13
> **Izza said:**
> Is there a way to override the GTK theme per-application? :confused:

Any help anyone could give would be most appreciated! Thanks!


No! some applications such as firefox can be done using the  userChrome.css, but most can not, any change in ~/.gtkrc-2.0 will affect all gtk2 programs, because they use the same calls.

---

### Post by alvinistic on 2008-03-14
This might be the one you are looking for:

GTK2_RC_FILES=path/to/gtkrc program

For example:
GTK2_RC_FILES=$HOME/.themes/Darkilouche/gtk-2.0/gtkrc f-spot

Anyway, taken from: [http://zeusville.wordpress.com/2007/05/15/changing-gtk-theme-for-a-specific-application/ ]("http://zeusville.wordpress.com/2007/05/15/changing-gtk-theme-for-a-specific-application/")

---

### Post by zz9pluralzalpha on 2008-03-26
Thank you.

Btw, if you want that in a desktop shortcut, you have to do:

sh -c "GTK2_RC_FILES=path/to/gtkrc program"

---

### Post by zz9pluralzalpha on 2008-03-26
With some additional checking, I've found it doesn't always work. On my system, it works with Darklooks and Divinornum, but not Aurora-Midnight. That is to say, when Aurora-Midnight is the system theme, the GTK2_RC_FILES over-ride is ignored. I have no idea why.

---

### Post by revertex on 2008-04-12
thank's alvinistic, i did it before but can't remember how.

I always use dark themes, actually im pretty confortable with neutronium, but some applications like meld and opera are unusable with this theme.

i wrote a litle bash script to lauch a app with a different theme, may be useful for lazy people like me.

i name it cleartheme, name it what you want, to use just type in a terminal
```
cleartheme mybuggyapp
``````
#!/bin/bash
# lauch a gtk application with a different theme
# set GTKRCFILE variable to your favourite theme
GTKRCFILE=Clearlooks
GTK2_RC_FILES=/usr/share/themes/"$GTKRCFILE"/gtk-2.0/gtkrc "$@"

```

---

### Post by paulrobert_a on 2008-07-16
You are my saviour, Thank You!

Open Office wasn't playing nice with NotXP GTK theme, menu colour being white on a light grey toolbar and drop menu's.  I Changed all the menu shortcuts with your script works like a charm.

Thank You again.

---

