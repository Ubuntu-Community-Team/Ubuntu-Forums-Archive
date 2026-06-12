---
title: "Memory leak with Compiz fusion"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by reddfox321 on 2007-10-08
I'm using Trevino's repository and I am up to date at this point.

When I installed CF I used
```
compiz --replace --indirect-rendering
```
to start it up and it worked fine.

When I installed the Fusion Icon the instructions I used erroneously told me to use
```
compiz-tray-icon
```
instead of
```
fusion-icon &
```

I'm a bit of a noob so I didn't understand (and still don't) understand the difference but there *is* a performance difference. When I try to use the Fusion icon it refuses to work correctly, I click it and CF automatically starts without giving me the menu of options. Not only that but CF starts without my saved settings and it becomes a resource hog using upwards of 180 MB of RAM. However when I start CF with 
```
compiz --replace --indirect-rendering
```
CF has my saved settings and behaves correctly.

So today I upgraded my AWN to .2 stable. Mind you I'm a noob and I was looking all over the internet for the dependencies and installed changed a bunch of things trying to get AWN installed.  I'm not sure if any of these could have messed up my CF install. Now when I use 
```
compiz --replace --indirect-rendering
```
to start CF there is an absurd memory leak and consequent lockup. CF doesn't even start. The terminal output says
```
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```
```
A handler is already registered for the path starting with path[0] = "org"
```
```
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```
for at least a hundred lines each. Any idea?


BTW, these are the changes I made to my system today
```
sudo apt-get install bzr
```
```
sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev 
```
```
libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0
```
```
libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf gnome-common python-dev python-gtk2-dev python-cairo-dev 
```
```
 python-gnome2-dev
```
```
sudo apt-get install python-dev
```
```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev

```
any ideas?

---

### Post by reddfox321 on 2007-10-08
Nothing, nobody have an idea?

---

### Post by reddfox321 on 2007-10-09
Wow, so nobody wants to help me out or knows how to help me out? So much for community

---

### Post by sludge99 on 2007-10-09
hi i think when you dont get a response its because no one here really knows the answer ive gotten that a few times it happens. im not a technical expert in compiz fusion although i do use it but doesnt Trevino make his packages for his repo from git. that might be a source of the poblem since git is a bit unstable. in any case i would suggest asking at the compiz fusion forums or get a dev on there irc to help you out i think [http://www.opencompositing.org/](http://www.opencompositing.org/) is the website which will link you.

or you can get a copy of gusty which has compiz-fusion installed by default and it appears to be rather stable which is what im doing atm although gusty is in beta for another week or two till it is stable.

---

### Post by reddfox321 on 2007-10-09
hey sludge, I'll do what you said and ask the compiz folks.

Thanks for replying!
**[COLOR="Red"]EDIT: SOLVED![/COLOR]**
I had to disable the Dbus plugin. You're right, I didn't know that the Trevino Repos were bleeding edge.
If anybody else is having this problem I suggest opening the compiz config settings manager and unchecking the DBus plugin.

Note that I did get this output
```
~$ compiz --replace
fuse: failed to exec fusermount: Permission denied
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

---

