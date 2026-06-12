---
title: "how to use multiple desktop environments?"
date: 2007-04-28
forum: Desktop Environments
---

### Post by Gray Fox on 2007-04-28
After I tried installing kubuntu-desktop with dodgy results I thought I'd ask first before trying again.

I was wondering how would I go about running multiple desktop environments (not simultaneous of course) on the same Ubuntu (Feisty Fawn 7.04) installation?

As I mentioned I tried installing kubuntu-desktop but ran into some problems, I think it was when it asked me if I wanted to use gdm or kdm as my default thingy and I choose kdm and it freaked out and I couldn't get back into my desktop.

I tried searching this forum and took a look at the wiki too but couldn't find what I was looking for so if I could either be pointed in the right direction for the info or if someone would like to share it that would be much appreciated!

I'm using the normal desktop ubuntu right now but I am interested in checking out KDE and Xfce to see what they have to offer and if maybe I may like them better.

---

### Post by 3rdalbum on 2007-04-28
Try installing kde-core instead of kubuntu-desktop.

You should be fine installing xubuntu-desktop, as it uses GDM as the login manager anyway.

Actually, you might be interested to know that you can run multiple DEs simultaneously. Log into Gnome, do a "switch user", and then at the GDM screen select KDE, and log in. Then Gnome will be on Control-Alt-F7, and KDE will be on Control-Alt-F8. You can switch user again to load XFCE, Window Maker, Enlightenment, or any other window manager. You can run them in whatever order you want.

There's also a program called xserver-xephyr (and another called xnest) which allow you to run new X sessions inside a window.

---

### Post by Gray Fox on 2007-04-28
> **3rdalbum said:**
> Try installing kde-core instead of kubuntu-desktop.

You should be fine installing xubuntu-desktop, as it uses GDM as the login manager anyway.

Actually, you might be interested to know that you can run multiple DEs simultaneously. Log into Gnome, do a "switch user", and then at the GDM screen select KDE, and log in. Then Gnome will be on Control-Alt-F7, and KDE will be on Control-Alt-F8. You can switch user again to load XFCE, Window Maker, Enlightenment, or any other window manager. You can run them in whatever order you want.

There's also a program called xserver-xephyr (and another called xnest) which allow you to run new X sessions inside a window.
Thank you for the reply!
I am installing kde-core right now, what would you suggest as far as acquiring xfce?

Those xephyr/xnest programs sound very interesting, do they cause a fairly substantial performance hit to use?

---

### Post by LuisGMarine on 2007-04-28
To install xfce all you would have to do is:

```
sudo apt-get install xubuntu-desktop
```

after that, simply go to System > Quit > Log Out. To log in to XFCE click on Sessions and choose XFCE.

Again if you are having trouble downloading all the packages, here is the full tutorial which also includes how to add the extra repos needed for the download.  Here is the tutorial:

[Click Here!]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_XFCE")

Good Luck

-LuisGMarine

---

### Post by steve8track on 2008-01-12
Here are some directions on how to open more than one window manager at the same time as an alternative to switching user:

1. Go to your home directory and backup then change/create a file called ".xinitrc" with the first line saying what second window manager you want to open. I have "exec /usr/bin/enlightenment" in that file.  Don't forget to put exec before the command for the desktop manager.
2. Press Ctrl+Alt+1 or some other number under 7 to look at your virtual consoles. Login to the console.
3. Type "startx -- :1" into the command line (you can replace the 1 with some other small number if it doesn't work). It will load the second window manager in Ctrl+Alt+9 or some other number greater than 7.  The :1 means send the command to that display, so this works for other programs as well once an x session is running on that display.

If you want more window managers open simultaneously, edit .xinitrc again after opening the second window manager and repeat the process with your other virtual consoles. Opening the same window manager twice might not work because certain files may be locked for the current session using them.

To leave the other desktop environments, I suggest using Ctrl+Alt+Backspace to kill the x on that display (it won't kill all of the sessions), because logging out when you started x from the command line may not work right.  Then type logout to log out your virtual terminal.

I hope this is helpful.

Steve

---

