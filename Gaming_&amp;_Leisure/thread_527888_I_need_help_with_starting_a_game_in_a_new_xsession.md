---
title: "I need help with starting a game in a new xsession"
date: 2007-08-17
forum: Gaming &amp; Leisure
---

### Post by Mogurijin on 2007-08-17
Hello, I'm fairly new to Ubuntu (about a week now), but I need some help getting Guild Wars (or any game for that matter) running in a new X session. My problem is the X session starts up then just sits there for  while. When I hit CTRL+ALT+Backspace, I see the following error in my terminal:

```
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
```

I'm using Ubuntu 7.04 Feisty Fawn, WINE 0.9.49, and the closed souce flrgx ati driver ( I don't know if this is causing any issues). Also, I don't know if it is the afore mentioned font thing, or some other error (I seemed to have fixed the other errors :)).

And here is my script:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac

# Goto game dir (modify as needed)
cd "/media/hdb1/Guild Wars/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "D:/Gw.exe"
```

And my font section in my xorg.conf file:
```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```

Hope that wasn't too long, I just wanted to be specific :)

---

### Post by Mogurijin on 2007-08-17
Well, I left it in the new Xserver to see if this Font issue would actually fix itself because I new it removed some things from another list (xorg.conf I think, but I can't be sure). However, nothing. Just the same thing I've been getting (black and white checkered background with an x cursor), even after sitting there for over two minutes. 

As to be expected, when I use CTRL+ALT+Backspace, I see the terminal. However, instead of canceling (CRTL+c) I waited for about one minute and got:

```

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

However, no matter how long I sit in this new Xserver a window never comes up, and this error only appears after being in my old xserverfor a little bit with out canceling the script.

Help would be nice. And I hope this is just a newb problem because I've only seen one or two other people have this problem, which never got fixed. I'm wondering if my ATI drivers are to blame?

EDIT: Also, I'm not using a 3d desktop environment such as beryl, compiz, or compiz fusion.

---

### Post by ominousluv on 2007-08-17
I'm getting the same problem, ATI 9800 with Envy drivers.

---

### Post by Mogurijin on 2007-08-17
What are envy drivers? Is that the flrgx stuff? Also if it is the ATI drivers, anyone know how to fix this problem?

---

