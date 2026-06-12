---
title: "Cannot see anything when I boot"
date: 2009-11-30
forum: Desktop Environments
---

### Post by rcrane on 2009-11-30
Hi All,

I'm running kubuntu 9.1 on a dell vostro.  Everything was fine until suddenly today my desktop environment began behaving strangely (I lost all program tabs on the bottom and top of the screen....along with all file menus across the top).  I rebooted the machine from the command line and since then I have been unable to get my machine to boot properly.

The boot menu comes up, now asking me to login at a terminal.  After this login, the system waits for about 5 seconds, then loads the login window.  At this point, if I login, the screen goes completely black.  I still have a mouse cursor, but nothing else. 

If I unplug the monitor and plug it back in, I can see the blue KDE desktop momentarily, but then it goes to black again. 

I had the feeling that it was the xorg file, so I tried to restore the /etc/X11/xorg.conf file to it's original state (dpkg-reconfigure xserver-xorg).  This did not solve any problems.  I had previously had difficulty getting dual monitors to work, but everything had been fine for a while.  

The only other things I should mention is that this occurred after installing quanta (apt-get install quanta).  When I launched quanta from the command line I lost all navigation/file menus.

The last thing I should mention, is that I have not been able to "lock" my screen for the past week or so before this happened.

Any advice or direction would be greatly appreciated.

Cheers,

R

---

### Post by benerivo on 2009-11-30
I'd probably try to set a couple of your kde config files back to their defaults. If you can use Ctrl+Alt+F1 to get to a terminal window then you could try to rename kdeglobals and kwinrc by doing...```
mv .kde4/share/config/kdeglobals .kde4/share/config/kdeglobals-old
```and...```
mv .kde4/share/config/kwinrc .kde4/share/config/kwinrc-old
```Then try and login (using Ctrl+Alt+F7 to get back to the login screen)

---

### Post by rcrane on 2009-12-01
Thanks for the advice.

I followed your instructions and now I'm able to see the desktop (blue background).

But I still don't see any of the menus (no taskbar, no kde menu button, etc)....so I can't even get a terminal to launch programs, etc.  Any more suggestions?  

Could you maybe explain what goes on in the startup process that is going wrong?

Thanks!

---

### Post by benerivo on 2009-12-01
It sounds as if the base window manager has loaded, but that the plasma element has failed. Plasma is what kde4 uses to draw desktop objects such as widgets, icons, the panel, etc. The startup process just begins all of the desktop elements and any startup applications such as a sound mixer, network manager, etc. It will use the saved settings in the home directory to load them with your own preferences such as window style, plasma style, icons style, etc..

So, i would do what you've just done, but now do it for the plasma configuration files in that ~/.kde4/share/config folder. The files you want to rename are```
plasma-appletsrc
plasma-dekstop-appletsrc
plasma-desktoprc
plasmarc
plasmoidviewer-appletsrc
```but it may just be easier to rename the whole config folder with```
mv .kde4/share/config .kde4/share/config-old
```and if that doesn't work, then rename the .kde4 folder to .kde4-old and when you login you'll have the default kde desktop, like the first time you logged in.

---

### Post by rcrane on 2009-12-01
I went ahead and just moved the whole directory

mv .kde/share/config .kde/share/config-old

but I still have the same problem.  I have a cursor and a desktop background (blue with out of focus white dots), but no menus, etc.

What else can I try?

Thanks again for your help

---

### Post by Zorael on 2009-12-01
Hmm, let's see if plasma has anything to say about it.

Hit Ctrl+Alt+F1 to hop to a console, and enter the following there.
```
DISPLAY=:0 konsole &
```
Then hit Alt+F7 to hop back to the graphical session. There should be a Konsole running there now. In it, run **plasma-desktop** and see if it outputs any interesting error messages.
```
plasma-desktop
```

---

### Post by darude on 2009-12-26
I ran into a similar problem, boot up and the plasma workspace crashed.

It was because of a new Analog Meter widget I've added. To fix, I edited the file...~/.kde/share/config/plasma-desktop-appletsrc file and removed any trace of that widget

Alt+F2 - konsole to bring up terminal

---

