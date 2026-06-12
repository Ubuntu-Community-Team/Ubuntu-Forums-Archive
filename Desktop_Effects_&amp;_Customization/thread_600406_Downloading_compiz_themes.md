---
title: "Downloading compiz themes?"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by bhouncy on 2007-11-02
Is there a site for downloading themes? I found one site [http://www.compiz-themes.org/]("http://www.compiz-themes.org/") but the files I've found are *.emerald format which I think are for beryl. Or am I doing something wrong?

Edit: I'm now on Gutsy.

---

### Post by renzokuken on 2007-11-02
compiz and emerald are essentially two different things. compiz on its own will use the default metacity window borders. you need to install emerald to get what you think of as beryl/compiz themes working

```
sudo apt-get install emerald
```
then start emerald
```
emerald --replace
```
then you can install themes/change themes via the Emerald Theme Manager in your System menu..........

to get emerald running instead of metacity by default stick "emerald --replace" in your Startup Sessions

[www.gnome-look.org](www.gnome-look.org) is one of the better sites for emerald themes

---

### Post by Forlong on 2007-11-02
There are no such things as "Compiz themes".
Compiz is "just" a window manager and doesn't take care of themes.

There are three window decorators for Compiz available:
**gtk-window-decorator** - uses Metacity themes for Compiz
**kde-window-decorator** - uses Kwin themes for Compiz
**emerald** - uses it's own themes

Emerald has been ported to Compiz, so it's safe to use those themes.
If you want to use either one of the other decorators, all you have to do is download themes the way you are used to and you will be able to use them with Compiz then.

---

### Post by bhouncy on 2007-11-02
Thanks people. I have the compiz fusion-icon which is making this a little easier. I've just upgraded my system and this is the first time I've had 3d rendering on any Linux. Oh the joy!

---

