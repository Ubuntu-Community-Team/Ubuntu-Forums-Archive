---
title: "default desktop environment"
date: 2013-02-08
forum: Desktop Environments
---

### Post by amhainen on 2013-02-08
> **Krytarik said:**
> GDM relies on the file "/var/cache/gdm/USERNAME/dmrc" to set the login options, always. Eventually, upon logging you in, it updates the - similar - file "~/.dmrc" in your home directory, and then updates its copy with it, therefore copying it.

But it can't do this if you remove the write permission from its file, thus leaving the session settings stored within it untouched until you re-enable the write permission again, or modify it via root access.

So, what you need to do is log in to your desired default session, and then remove the write permission with a command like this:
```
chmod 444 /var/cache/gdm/USERNAME/dmrc
```To re-enable the write permission again, run a command like this:
```
chmod 644 /var/cache/gdm/USERNAME/dmrc
```Of course, you can also do this through the right-click menu of Nautilus if you like.

Greetings.


Hi Krytarik,

I'm trying to figure this out for 12.04 with GDM:

[http://ubuntuforums.org/showthread.php?t=2113208](http://ubuntuforums.org/showthread.php?t=2113208)

I'd like "Gnome Classic" (gnome-fallback) to be the default desktop environment at the GDM login.

I didn't find anything (directories or files) in /var/cache/gdm/. I've tried adjusting ~/.dmrc with either Session=gnome-fallback or Session=gnome-classic, but those didn't work.

As I mentioned in the thread I started, I have GDM on 12.04 instead of LightDM.

Thanks so much!

---

### Post by furything on 2013-02-08
Hi amhainen):P
What is in /var/cache?
mine is lightdm
path is  /var/cache/lightdm/dmrc/user.dmrc

Have you tried going through all directories ending in dm?

---

