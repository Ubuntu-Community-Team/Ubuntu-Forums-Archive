---
title: "Hardy upgrade - Nautilus folder thumbnails same size as normal folder icons"
date: 2008-05-20
forum: Desktop Environments
---

### Post by netron on 2008-05-20
my upgrade from gutsy to hardy has been pretty flawless , apart from one really annoying problem.

i regularly thumbnail my music folders with album covers or band photos, and in Gutsy, these were displayed a bit bigger than normal folders.

But after the upgrade the thumbs ended up the same size as the folders, which isn't great visually - and increasing the overall icon size just makes ALL the icons go bigger.

see screenshots below to see what i am on about:

at nautilus "view as icons" 100%:
[IMG]http://i25.tinypic.com/ebc16s.jpg[/IMG]


and then if i up it to 150%:
[IMG]http://i25.tinypic.com/25z2whw.png[/IMG]



Is there some gconf-editor setting that i need to set maybe?

has anyone else encountered this after a gutsy->hardy upgrade?

---

### Post by netron on 2008-05-28
bump.
i was just wondering if anyone else has encountered this problem - and if so, what was the solution?

In Gutsy , this wasnt an issue.

---

### Post by sayakb on 2008-05-28
Confirmed. I too have this problem. Doesn't seem like an upgrade problem, but a bug in Hardy, I guess.

---

### Post by Nicksha on 2008-06-22
This annoys me too. Fortunately, I don't have many custom folder icons, so what I did was the following:

In "/home/yourusername/.nautilus/metafiles" (obviously, substitute "yourusername" with... well, your username) there's a bunch of configuration files for your folders. When you find the one that pertains to the **parent folder** of the folder which has been customized, open it. In that file, you'll find the line that looks something like this: ```
<file name="Basement%20Jaxx" custom_icon="path_to_your_icon"/>
``` Just before the "/>" tag, add ```
icon_scale="2.0"
``` You can put any other value, of course. You have to repeat that for every customized folder, so it's not a solution if you have a lot of folders like that. Also, to see the effects of this workaround, you have to restart (kill) Nautilus.

There's got to be a system-wide solution for this (maybe it's got something to do with icon themes), but until it's found this may work for some of you.

---

### Post by vitko on 2009-03-24
Welcome to the club. Thumbnailing folders with custom image is broken in nautilus since 2.20.

See [http://bugzilla.gnome.org/show_bug.cgi?id=524392](http://bugzilla.gnome.org/show_bug.cgi?id=524392)

Hope someone brave will fix this problem soon.

---

