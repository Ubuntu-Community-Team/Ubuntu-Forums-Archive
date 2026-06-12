---
title: "Post LXDE config files, please? Trying to use LXSession for custom desktop"
date: 2012-02-25
forum: Desktop Environments
---

### Post by gldearman on 2012-02-25
Hi, all,

I don't actually use LXDE, but I need some help with one of its components — LXSession session manager.

I am trying to assemble a custom desktop environment as an alternative to Gnome.  I'd like it to be run under a session manager.  I picked LXSession because it's lightweight, has few dependencies, and seems easy to configure.

I found a number of tutorials online, and they all gave slightly different but similar steps.  But I can't get this to work.  I try to log in to my custom session, and it crashes and returns immediately to the gdm greeter.

So, I have two questions, and I'm hoping a current LXDE user can help me figure this out.

1) This simplest question to ask (but maybe hardest to answer): Does anyone already know how to configure LXSession to launch a custom session? If so, could you tell me? All I'd like to include in the custom session for right now is Compiz, Avant Window Navigator, and Guake.

2) If no one knows that, can a current LXDE user just post for me the contents of their LXSession config files, and maybe I can figure it out from there? A lot of the online instructions include some variant of "Just go into these files and change all references to LXDE to refer to your custom desktop environment instead." Only, I don't have these files, I have to write them from scratch. I could download the entire LXDE meta-package, but it seems excessive to just have a look at the LXSession config files.

What I'd like to see are the contents of:

/usr/share/xsessions/LXDE.desktop (if you have it, this is for launching from gdm)
/usr/bin/startlxde
/etc/xdg/lxsession/LXDE/autostart
/etc/xdg/lxsession/LXDE/config

I would really appreciate an LXDE user posting those for me; it would be a big help.

Thanks!

---

### Post by Rodney9 on 2012-02-25
This is my desktop.conf from Lubuntu 11.10 lxsession

What window manager are you using ?

Something like this might help - 

[http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)

```
[Session]
window_manager=openbox-lxde

[GTK]
sNet/ThemeName=Clearlooks
sNet/IconThemeName=Faenza-Darkest
sGtk/FontName=Sans 10
iGtk/ToolbarStyle=3
iGtk/ButtonImages=1
iGtk/MenuImages=1
iGtk/CursorThemeSize=18
iXft/Antialias=1
sGtk/ColorScheme=
iGtk/ToolbarIconSize=3
iNet/EnableEventSounds=1
iNet/EnableInputFeedbackSounds=1
iXft/Hinting=1
sXft/HintStyle=hintfull
sXft/RGBA=rgb

[Mouse]
AccFactor=20
AccThreshold=10
LeftHanded=0

[Keyboard]
Delay=500
Interval=30
```

---

### Post by gldearman on 2012-02-25
> **Rodney9 said:**
> This is my desktop.conf from Lubuntu 11.10 lxsession


desktop.conf?
Is that located at /etc/xdg/lxsession/LXDE/desktop.conf?
I think that's my problem.  The documentation I got from LXDE.org indicated that the file should be called "config." If it's actually supposed to be called "desktop.conf" I can see why that wouldn't boot.

> **Rodney9 said:**
> 
What window manager are you using ?


I'm attempting to use Compiz.

> **Rodney9 said:**
> 
Something like this might help - 

[http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)


I didn't realize that there was a minimal Ubuntu iso available, and that may be useful to me in the future.

I don't think it'll help in this case, though.  I'm not trying to replace Gnome or create a minimal install, just create a second desktop environment in addition to Gnome. 

The name "desktop.conf" was very helpful, though.  And so were the results I got from googling it.  I'll try it as soon as I get back to the computer I'm trying to do this on.  Thanks!

---

### Post by gldearman on 2012-02-25
OK, renaming my /etc/xdg/lxsession/config file to /etc/xdg/lxsession/desktop.conf didn't help.  Neither did copying yours, pasting it to mine, and changing nothing except the name of the window manager to "compiz."

So, here are the complete contents of the config files that I have.  I may be missing a file, or maybe there's an error in one of these.

/usr/share/xsessions/custom.desktop
```
[Desktop Entry]
Encoding=UTF-8
Name=custom
Comment=This is a custom desktop environment under development
Exec=/usr/bin/startcustom
Type=Application

```

I'm at my wits' end, and would certainly appreciate any help anyone can offer.

Thanks!

/usr/bin/startcustom
```
#!bin/sh
exec /usr/bin/lxsession -s custom

```

/etc/xdg/lxsession/custom/desktop.conf
```
[Session]
window_manager=compiz --use-root-window ccp

```

/etc/xdg/lxsession/custom/autostart
```
@smproxy
@avant-window-navigator
@guake

```

---

### Post by gldearman on 2012-02-26
OK, I now know that this is not a dependency issue.  I went ahead and installed LXDE.  With that installed, LXSession will launch LXDE just fine, but still won't launch my custom environment.  So, it's gotta be something in the config files.

I'm going to go through the LXSession config files line-by-line, changing things one at a time until there is no LXDE left, and everything is changed to the custom environment I want.  But that's going to be a long and tedious process.  So … if anyone can help me out before then, I'd appreciate it.

Thanks!

---

### Post by gldearman on 2012-02-26
OK, I got it.

I needed to change my /usr/bin/startcustom to read:

```
#!bin/sh
exec /usr/bin/lxsession -s custom -e custom
```

That's all it took.

---

