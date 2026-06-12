---
title: "How to change window manager in Gnome?"
date: 2010-05-16
forum: Desktop Environments
---

### Post by david.given on 2010-05-16
I would like to change to use a different window manager (as Metacity has persistent bugs and annoys me). How can I do this?

I've tried setting the WINDOW_MANAGER environment variable --- no effect.

The gconf keys in the obvious place are marked as deprecated and have no effect.

There is no .session file I can modify.

There must be *some* way to do this! Can anybody enlighten me?

---

### Post by hoooootz82 on 2010-05-16
You can switch the window manager from command line. For many windows manager its just a "--replace" flag, such as
```
compiz --replace
```
or
```
metacity --replace
```

I have never tested this with managers other than compiz and metacity, but fusion icon can switch windows managers fairly easily as well. Hope this helps.

---

### Post by david.given on 2010-05-17
But I have to do that every time I log in.

How can I actually *change* the window manager used by my login session on a permanent basis?

---

### Post by david.given on 2010-05-20
Does really nobody know how to do this? It ought to be really simple!

---

### Post by Nythain on 2010-05-20
create a simple script that runs every time you log in... you could create a new Xsession .desktop file that runs what you want it to probably possibly... not sure, i dont use gnome, or gdm for that matter

---

### Post by Nythain on 2010-05-20
Sort of bad form to link to another distro's wiki, but the ArchWiki cover's running Openbox from inside gnome...

i would follow this procedure replacing openbox with whatever window manager you use

[http://wiki.archlinux.org/index.php/Openbox#GNOME](http://wiki.archlinux.org/index.php/Openbox#GNOME)

---

### Post by david.given on 2010-05-20
But both those approaches involve starting Metacity, and then later running 'xfwm4 --replace' to replace Metacity with another window manager. I don't want to do that --- not only will it just make login times longer and generally complicate matters, but I'll get Metacity's window placement behaviour for apps that start at about the same time as the new window manager.

All I want to do is to find Gnome's window manager setting and change it from Metacity to XFWM4. This should not be hard.

Unless, of course, they've decided not to make it configurable, and have instead hard-coded it to Metacity....

---

### Post by ogilvierothchild on 2010-11-19
Set this key in gconf

/desktop/gnome/session/required_components/windowmanager

i.e. type Alt-F2, then type "gconf-editor", navigate to this key, then type "openbox" or whatever instead of metacity.

---

### Post by david.given on 2010-11-19
That was one of the things I tried --- didn't work, I'm afraid. I have vague memories of finding rumours on the intertubes that that key was deprecated and had no effect, but I can't track them down now.

---

### Post by hhh on 2010-11-19
You're trying to use xfwm4 in Gnome? It begs the question, "Why not switch to Xfce entirely?", but anyway...
[http://programmingforchildren.blogspot.com/2009/10/fastest-way-to-replace-gnomes-metacity.html](http://programmingforchildren.blogspot.com/2009/10/fastest-way-to-replace-gnomes-metacity.html)

As I understand it, the only effect of changing the gconf key in /desktop/gnome/session/required_components/windowmanager/metacity to anything else (except maybe compiz --replace or compiz-manager) is that metacity won't start, in which case you can leave the "--replace" off of the xfwm4 startup command. I can't test this for you as I've deleted my testing partitions and am using Xfce full time.

-edit- I see that there is this key also which you should probably change...
/desktop/gnome/applications/window_manager/current

More stuff I found...
[http://chad.glendenin.com/metacity/xfwm4.html](http://chad.glendenin.com/metacity/xfwm4.html)
[http://ubuntuforums.org/showthread.php?t=610606](http://ubuntuforums.org/showthread.php?t=610606)
[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/593465](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/593465)
Finally, from here...
[http://xfce-look.org/content/show.php?content=114712&PHPSESSID=b8a1835b627a64adb6382ade95fbd6cc](http://xfce-look.org/content/show.php?content=114712&PHPSESSID=b8a1835b627a64adb6382ade95fbd6cc)
> In order to replace Metacity with XFWM4 in GNOME, do the following:
0) Install xfwm4 package trough your package manager (or compile it, if you really want to :)
1) Run gconf-editor (trough terminal or alt+f2 launcher).
2) Go to /desktop/gnome/session/required_components/windowmanager section.
3) Change value of "windowmanager" key to anything beside metacity (metacity-not for example, so you can easily bring back default value).
4) Close gconf-editor.
5) Launch gnome-session-properties.
6) Click "add" button.
7) In "name" field add XFWM4 (or anything you want, it's just a name).
8) In "command" field add "xfwm4" (without quotes).
9) now log out and log in - you should be running XFWM4 instead of Metacity now.

To change theme and basic settings of XFMW4, launch xfwm4-settings.

If you wan't to bring Metacity back, just remove or deactivate xfwm4 entry from gnome-session-properties and change windowmanager key value in /desktop/gnome/session/required_components/windowmanager section back to metacity (using gconf-editor).

---

