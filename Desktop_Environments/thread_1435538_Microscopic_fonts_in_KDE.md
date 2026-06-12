---
title: "Microscopic fonts in KDE"
date: 2010-03-21
forum: Desktop Environments
---

### Post by pixel :-) on 2010-03-21
Wine did something, and now system fonts are microscopic, to the point i can't read them. I can fix this by restarting my session, but i don't what too.

Can you give me the exact position, of where we change the font size, i can't read anything. Even parts inside this webpage.

---

### Post by phibxr on 2010-03-21
> **pixel :-) said:**
> Wine did something, and now system fonts are microscopic, to the point i can't read them. I can fix this by restarting my session, but i don't what too.

Can you give me the exact position, of where we change the font size, i can't read anything. Even parts inside this webpage.

It sounds like your DPI has been altered.

Could you perhaps log in using another window manager, or log directly into console mode, and make a backup-directory in your Home-directory and move all .kde* content into it?

```
~$ mkdir backup
~$ mv .kde* backup

(log in and investigate)

~$ mkdir backup2
~$ mv .kde* backup2
~$ mv backup/.kde* ./
```

That would hopefully reset all of your KDE-settings and let you investigate where and how to change your settings before moving the content of the backup-directory back after cleaning up the newly created .kde-content.

This might not be the best solution, but as noone else has answered I guess you might need something at least. If you can read it, that is. :)

---

### Post by hotelrooms on 2010-03-22
When I set DPI to 75 (which should be "correct" and displays the KDE fonts the right size) everything in Openoffice was microscopic.

---

### Post by Zorael on 2010-03-23
Isn't 96 the de-facto default DPI? Perhaps the KDE DPI setting isn't being properly translated into a GTK setting, and you have very small font sizes set up in KDE to compensate. Those sizes do get translated however and OpenOffice.org ends up using those.

I always edit kdm's configuration file to pass a -dpi argument to the X server, enforcing it.

In **/etc/kde4/kdm/kdmrc** under the section **[X-:*-Core]**;
```
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=-br -nolisten tcp **[COLOR="Green"]-dpi 96[/COLOR]**
```
Without that, the fonts in kdm are either microscopic or huge on my two machines. With it, everything behaves as it should. I think my font sizes are at 10px for normal fonts, 8px for small.

---

