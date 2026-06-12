---
title: "GNOME splash screen screwed up."
date: 2005-10-31
forum: Desktop Environments
---

### Post by angrykeyboarder on 2005-10-31
[FONT=Verdana]and I don't know how to undo it (especially since I don't know how I
messed it up in the first place)

I'd been switching my GNOME splash screens via the
gnome-splashscreen-manager.

Suddenly a few days ago I'd noticed a splash screen appeared out of
nowhere. It was not one I'd installed.  It's got the Debian logo on it.
I checked and indeed it's not one of those I have in my
splash-screen-manager application.

So I did a bit of hunting and came across  /etc/alternatives/desktop-splash and /var/lib/dpkg/alternatives/desktop-splash
In the second one is a list of 4 splash screens that I know nothing about.
Among those is the mystery splash screen I mentioned previously.  The first is an executable file

I'd love to get rid of all of this.  Does anyone have any idea what
package(s) they are part of or how I could otherwise get rid of it and restore my own splash screens?

And FYI, Gconf has noting to do with this. Gconf still shows the splash screen I should be seeing vs. the one I'm actually stuck with. Changing it has no effect.

Thanks.

Regards,[/FONT]

---

### Post by SilentCacophony on 2005-10-31
Hi. I don't use gnome-splashscreen-manager, but you may want to try checking it out by hand. I don't know if that app changes the way it normally works, though.

Anyway, there is a directory where ubuntu looks for *ubuntu-splash.png*, which by default is linked to *gnome-splash.png*. You may change that link to point to any other file. For example, I've changed mine to point to *bluebuntu-splash*, instead of the default. See how I check it:

```
brian@ubuntu:~$ **ls -l /usr/share/pixmaps/splash**
total 264
-rw-r--r--  1 root root  63426 2005-10-28 22:40 bluebuntu-splash
-rw-r--r--  1 root root 193367 2005-09-06 07:19 gnome-splash.png
lrwxrwxrwx  1 root root     16 2005-10-28 22:41 *ubuntu-splash.png* -> bluebuntu-splash
```

You should be able to see what it's linked to by doing as above. To manually change it:

```
sudo ln -sf <path_to_new_image> /usr/share/pixmaps/splash/ubuntu-splash.png
```

Maybe that can shed some light on it.

---

