---
title: "Gnome shell will not start......."
date: 2013-02-14
forum: Desktop Environments
---

### Post by greggc2006 on 2013-02-14
Can anyone help me diagnose and fix this error.

I have been using gnome shell for ages now and haven't recently made and changes AFAIK!! A couple of days ago I suspended my laptop, when I powered it up the next morning it booted to a login screen rather than a lock screen, when I entered my password it took forever to draw the desktop background, it then drew the icons and stopped. I was left with a desktop background, desktop icons and a mouse pointer. The mouse pointer was moving fine but nothing responded to clicks, there was no evidence of gnome-shell running at all and my startup applications didn't seem to be starting.

I have tried logging into other DE's, 3D unity and gnome classic seem to have the same issues, 2D unity is working as is gnome classic (no effects).

I have disabled all my startup apps and even uninstalled 'realtime sunlight wallpaper' to no avail.

I have removed the following folders in the hope they contained the error, again to no avail:-

~/.local/share/gnome-shell
/usr/share/gnome-shell

I have just moved them so can easily put them back.

Please help, I am desperate to get gnome-shell back, it is where I feel happy!!

---

### Post by kc1di on 2013-02-14
Though I haven't used gnome shell in awhile , it sounds like a Compiz 3d problem not the fault of the shell itself. 

you might want to try uninstalling and reinstall compiz and it's associated files. especially compiz-gnome

just a guess though good luck

---

### Post by waldherrvonbirnbaum on 2013-02-14
is this helpful?
[http://ubuntuforums.org/showthread.php?t=2115873](http://ubuntuforums.org/showthread.php?t=2115873)

or did you reconfigure your X?
```
#  dpkg-reconfigure xserver-xorg
```

---

