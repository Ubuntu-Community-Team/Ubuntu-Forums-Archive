---
title: "Debian + Openbox, someone guide me in the right direction :D"
date: 2007-11-30
forum: Debian
---

### Post by staticvoid on 2007-11-30
So I plan on doing a clean install of debian Etch

then I will install xorg

then openbox

correct?

Then I want to get conky and a simple theme. I notticed at box-look.org that the themes for openbox had like... drop shoddows underneath the windows. Is this because they are using compiz too or something?

and there is a dif between a windows manager and a Desktop Environment

is openbox the windows manager?? should i get gnome or something? or fluxbox...?

help me out here :D

sv

---

### Post by pelle.k on 2007-11-30
Openbox is a window manager, just like metacity in gnome, or kwin in kde. Kde and gnome are DE:s.
Openbox is very "bare". You will have to do some "magic" that the DE:s normally do for you.

This is a ubuntu guide, but the basics should still apply and at least give you some clues on how to start a panel etc at login;
[http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox+howto](http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox+howto)

ps. the "shadow effect" is from using xcompmanager...

---

### Post by staticvoid on 2007-11-30
aha! thank you. that looks like a very practical guide.

sv

---

### Post by urukrama on 2007-11-30
Openbox is a window manager, as it only manages the windows and not the desktop, panels and the mounting of volumes, etc. For those tasks you can use separate applications in Openbox.

Have a look [here]("http://www.psychocats.net/ubuntu/minimal#barebones") to setup a minimal install.

Then have a look at [my guide]("http://urukrama.wordpress.com/2007/11/26/an-openbox-guide/") to install and configure Openbox. It tells you how to install Openbox, but also how to use panels, desktop wallpapers, etc. It also mentions drop shadows and the like. It probably will be useful.

Both guides are for Ubuntu, but most of it should apply for Debian as well.

---

### Post by staticvoid on 2007-12-01
Ok, so I can use different apps to mount usb drives and such in openbox?

does it come with a terminal windows at least??

I read on the web site that you can do a minimal install, without a desktop enviorment or whatever. I was interested in this since it seemed like it would be super fast.


sv

---

### Post by D-EJ915 on 2007-12-01
Thunar can do volume management, just install thunar-volman then go into the preferences and enable it, you have to have hal too but it should probably already be installed...I don't remember

---

### Post by staticvoid on 2007-12-01
ok, so, so far,
-openbox
-thunar
-thunar-volman
-conky
-pymenu
-obmenu
-feh

for a quick systme for a guy who does n't know xml?

sv

---

### Post by urukrama on 2007-12-01
Yes, that should do. Openbox isn't that difficult, but you need to get used to it. That guide I linked to earlier should help getting you started.

As Openbox is a window manager, it doesn't come with a terminal, but there are plenty of terminals you can use: xfce4-terminal, urxvt, Sakura, gnome-terminal, etc.

If you have a running Ubuntu or Debian system, just install Openbox before you do your command line install and explore the possibilities. Then, if you like it, make the jump and reinstall your system if you so desire.

---

### Post by staticvoid on 2007-12-01
what terminal would you recomend? What opens the fastest?


I plan on installing Debian with XFCE and then install openbox. Then maybe I'll remove some stuff from xfce.

**What windows manager does XFCE use?**

I can't get my wireless working, perhaps with a gui it will be easier.  :(

sv

---

### Post by staticvoid on 2007-12-01
Oh,
 it uses Xfwm4

nevermind,

sv

---

### Post by init1 on 2007-12-01
> **staticvoid said:**
> what terminal would you recomend? What opens the fastest?


I plan on installing Debian with XFCE and then install openbox. Then maybe I'll remove some stuff from xfce.

**What windows manager does XFCE use?**

I can't get my wireless working, perhaps with a gui it will be easier.  :(

sv

XTERM is a good, fast option but its very simple. If you want more features try xfce4-terminal

---

### Post by staticvoid on 2007-12-02
> **urukrama said:**
> Openbox is a window manager, as it only manages the windows and not the desktop, panels and the mounting of volumes, etc. For those tasks you can use separate applications in Openbox.

Have a look [here]("http://www.psychocats.net/ubuntu/minimal#barebones") to setup a minimal install.

Then have a look at [my guide]("http://urukrama.wordpress.com/2007/11/26/an-openbox-guide/") to install and configure Openbox. It tells you how to install Openbox, but also how to use panels, desktop wallpapers, etc. It also mentions drop shadows and the like. It probably will be useful.

Both guides are for Ubuntu, but most of it should apply for Debian as well.

Hey, i've followed your guide but for some reason I cannot get my icons to set right when i start up. here is my gtkrc-2.0.mine file:

```
gtk-icon-theme-name = "Tango-Original"
gtk-theme-name = "Clearlooks"
```

and my gtkrc-2.0 file:

```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/Clearlooks/gtk-2.0/gtkrc"

style "user-font" {
	font_name = "UnDotum 10"
}

widget_class "*" style "user-font"

gtk-font-name="UnDotum 10"

include "/home/nathan/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

I keep having to run gnome-appearance-properties to change my icons to my tango theme.

could somebody help me :) or point me in the right direction?

sv

---

### Post by Tenken on 2007-12-02
Try renaming your file to just .gtkrc.mine, that works for me. Another program I would recommend is gtk-chtheme. You can use that to change your gtk theme without editing a config file.

---

### Post by staticvoid on 2007-12-02
that did the trick, all my icons and everythin g load automatically. :)

sv

---

