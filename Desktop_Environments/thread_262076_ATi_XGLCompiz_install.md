---
title: "ATi XGL/Compiz install"
date: 2006-09-21
forum: Desktop Environments
---

### Post by kaisa on 2006-09-21
So, my bout with XGL/compiz round two, and I believe compiz wins this round again. 

Everything is just peachy when I install fglrx drivers for my X800 pro. fglrxinfo displays the right information and I am able to run 3d accelerated games (like warsow). The problems hit on the XGL/compiz install. I followed [http://www.ubuntuforums.org/showthread.php?t=168618](http://www.ubuntuforums.org/showthread.php?t=168618) to the T. 
Everything looks like it went well UNTIL I attempt to logout and log back in to XGL. The desktop loads, then theres a quick flash and I notice that the desktop switcher no longer works. Also, any new windows that are opened are jammed up into the left hand corner of the screen...underneath the top panel bar! It's impossible to move the windows...even when you right click and select move on them.

Also, I tried checking out the compiz plugins using gconf-editor, but the only option i see in there is audible_bell. Apparently theres supposed to be more.

Trying to get gset-compiz is turning out to be tough. I tried it as an alternative to gconf, but when i try to apt-get it, I get:
```
Reading package lists... Done
Building dependency tree... Done
Package gset-compiz is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gset-compiz has no installation candidate

```

And one more thing...

In the startcompiz shell script that im using:
```
killall gnome-window-decorator 
wait
gnome-window-decorator & DISPLAY=:1
compiz --replace gconf
#fixes the shift-backspace bug
xmodmap /usr/share/xmodmap/xmodmap.us
```
I hear that in later versions of compiz that
```
compiz --replace gconf
```
should actually be
```
compiz --replace csm
```
can anyone confirm/deny this?

Gah...im frustrated but im not giving up. Does anyone have insight into this?

Thanks!

---

### Post by thater on 2006-09-21
I'm currently having precisely this exact same issue.  So far I haven't come across any solutions.  I'm running an X200 Mobile with the ATI fglrx drivers provided on the Synaptic repositories.  So I'm guessing it's an issue with Mobile ATI cards, or possibly with the drivers.  I can also run OpenGL accelerated games reasonably well, and receive the satisfactory information when I enter fglrxinfo so I know I have the acceleration working.

I'm able to alt-right click windows and set their transperancies, brightness, and other things but I can't move any of the windows, or change desktops.

---

### Post by kaisa on 2006-09-21
quick bump to the top, i'd really love to figure out whats going on here.

---

