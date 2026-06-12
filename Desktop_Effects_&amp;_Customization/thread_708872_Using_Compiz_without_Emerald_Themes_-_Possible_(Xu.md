---
title: "Using Compiz without Emerald Themes - Possible? (Xubuntu)"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by KenBW2 on 2008-02-26
I think I want the opposite to everyone else here, but nevermind.
What I want is all the animated effects that come with Compiz, but I don't like all the bling that the emerald themes have. I just want the basic XFCE theme back!
I'm pretty sure this is possible (I had a similar setup on my other Ubuntu box) and want it on my EeePC running EeeXubuntu.

I've tried in terminal [FONT="Courier New"]xfwm4 --replace[/FONT] and it tells me I already have a window manager running.

Help much appreciated!

---

### Post by fracturedmorals on 2008-02-26
You can use gtk-window-decorator, which gives you metacity themes....

just:
```
sudo apt-get install -y compiz-gnome && sudo apt-get remove -y emerald
```

then:
```
gtk-window-decorator --replace
```

Extract any metacity themes to ~/.themes

That will get rid of emerald and give you gtk-window-decorator

you can then change settings from the gconf-editor application.

Set gtk-window-decorator to use metacity themes with:
apps>gwd>use_metacity_theme

Change the metacity theme with:
apps>metacity>general>theme

Of course if you already have gnome installed on your system somewhere, you can configure the themes themselves from:
```
gnome-appearance-properties
```

Edit:
Just use gconf-editor :\

Hope this helps

---

### Post by Islington on 2008-02-26
what is the default window manager of xfce?

If it is as you say in your post: xfwm4 then in CCSM>>Window Decoration>>General

couldn't you put in ```
xfwm4 --replace
``` in the "**command** " box?

My apologies if this is totally wrong, I have never used xfce.

---

### Post by fracturedmorals on 2008-02-26
Compiz, itself is a window manager, and unfotunately does not handle XFWM decorations yet.

:(

---

### Post by KenBW2 on 2008-02-27
@islington
I tried that one, it just ignores me and loads Emerald anyway

@framcturedmorals
Thanks! Using the GTK window decorator worked :)

---

