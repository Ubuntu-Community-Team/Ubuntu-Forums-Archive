---
title: "No login screen at boot"
date: 2012-04-20
forum: Desktop Environments
---

### Post by montgoss on 2012-04-20
I've messed up my Ubuntu 11.10 install. It boots part of the way, but instead of going to the login screen, after the progress screen with the blinking dots, I get a black screen with some text output. The last thing it says is "stopping system V runlevel compatibility    [OK]".

If I drop to a console (Ctrl-Alt-F2), login, and run 'startx', I can get a GUI up (which is how I was able to get this browser open). However, I don't have any taskbar or menus. This is probably because I followed some random instructions found via Google to remove Unity. Well, I think I removed Unity, but something is still trying to launch Unity instead of the gnome-shell (or whatever I really want).

So, I'm hoping there's some simple configuration thing I need to run that will restore the gnome classic desktop environment (not Unity). Anyone know what I need to do?

Thanks in advance.

---

### Post by grahammechanical on 2012-04-20
Here is where you say the cause of the problem

> I followed some random instructions found via Google to remove Unity. Well, I think I removed Unity,

Ubuntu uses Compiz and Unity in enhanced or 3D mode and metacity and Unity in 2D or fallback mode.


As far as I know people do not remove Unity, they install Gnome Session Fallback and then select it at the log in screen.

See this forum sticky thread:

[http://ubuntuforums.org/showthread.php?t=1859961]("http://ubuntuforums.org/showthread.php?t=1859961")

As you are not sure what you removed it might be simpler to re-install without formatting. Backup your data first.

Regards.

---

### Post by tmaranets on 2012-04-20
Don't try to mess with your Ubuntu stuff, sometimes it might not even be reversible. You probably tried "startx" if you have the capability to type.  Try installing Ubuntu again, and don't mess up the startup installation.

---

### Post by montgoss on 2012-04-20
> **tmaranets said:**
> Don't try to mess with your Ubuntu stuff, [...]

Uh, what's the point of linux if I can't mess with it??  No, I will continue to mess with it until I get it how I like it. The defaults used to be mostly fine, but the update-manager kept saying that whatever v10 that I was on was no longer supported. So, I was coerced into upgrading and I'm just trying to get a normal desktop back. Perhaps I need to switch away from Ubuntu? I'm hesitant to, since it's served me well for years... 

Anyways, since I didn't get any responses on how to restore the login screen, I re-installed fresh to v11.10. And since my home drive is on a separate partition, I didn't need to backup.

I'll take a look at those other threads and see if there's a way to get back to normal without dumping Ubuntu entirely. Thanks for the link.

---

