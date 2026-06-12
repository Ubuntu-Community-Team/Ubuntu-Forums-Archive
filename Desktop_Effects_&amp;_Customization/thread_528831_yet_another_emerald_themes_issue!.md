---
title: "yet another emerald themes issue!"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by Alex&amp;Linux on 2007-08-18
Hey all!
Ive just installed Feisty on my new intel macbook, and have run into a problem with emerald themes rendering with compiz fusion.

The error output follows:

```
alex@Linux:~$ emerald --replace

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

```

Its running, as pidof shows it, but it just wont render!
I assume that there may be some edits to xorg.conf coming up, but cant locate any advice in this regard!

---

### Post by realvz on 2007-08-18
seems like you need to upgrade your version of emerald..

how did you install CF....is you did it using Trevino's repo...

then uninstall emerald and then reinstall emerald

alternatively you can also use beryl-manager to force emerald...

hope ti works for you.

---

### Post by walkerk on 2007-08-18
> **Alex&Linux said:**
> Hey all!
Ive just installed Feisty on my new intel macbook, and have run into a problem with emerald themes rendering with compiz fusion.

The error output follows:

```
alex@Linux:~$ emerald --replace

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7023): Wnck-WARNING **: Unhandled action type (nil)

```

Its running, as pidof shows it, but it just wont render!
I assume that there may be some edits to xorg.conf coming up, but cant locate any advice in this regard!

is compiz fusion loaded before you try emerald --replace?
```
compiz --replace

emerald --replace
```

also what version of emerald are you using?
```
sudo aptitude show emerald
```

additionally ensure your libwnck is current
```
sudo apt-get update

sudo apt-get install libwnck18 libwnck-common libwnck-dev
```

---

### Post by Alex&amp;Linux on 2007-08-18
Thanks for the replies!
Like I said, emerald is "running", it just doesnt render!
I have tried using --replace, and when I use beryl-manager to affect this, though I can select the window manager and decorator, this disables the fusion plugins in compiz!
While everything works perfect while using beryl!

Here is the output showing the version:

```
alex@Linux:~$ sudo aptitude show emerald
Package: emerald
State: installed
Automatically installed: no
Version: 0.3.0+git20070728~3v1ubuntu1
Priority: optional
Section: eyecandy/x11
Maintainer: Trevi - 3v1n0 <trevi55@gmail.com>
Uncompressed Size: 967k
Depends: libatk1.0-0 (>= 1.13.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.0),
         libdecoration0, libemeraldengine0, libfontconfig1 (>= 2.4.0),
         libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>= 2.10.3), libpango1.0-0 (>=
         1.16.2), libwnck18 (>= 2.15.90), libx11-6, libxcursor1 (> 1.1.2),
         libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxrandr2 (>=
         2:1.2.0), libxrender1
Recommends: emerald-themes, compiz | beryl
Conflicts: gcompizthemer, cgwd
Replaces: gcompizthemer, cgwd
Provides: cgwd, gcompizthemer
Description: Decorator for Compiz and Beryl
 This package provides a decorator for composite managers and a themer
 application
```

Ive run into this on a friend's PC, no problems on mine!
This one is really annoying!

---

### Post by Alex&amp;Linux on 2007-08-19
Hey all, looks like for me it was one of those situations where the simplest solutions are overlooked.

There is a "window decorations" plugin that was deselected, and I feel like absolute rubbish.

But at least its working! Thanks for your time.

---

### Post by realvz on 2007-08-19
great news...

we should probablhy make a sticky for all window manager issues with compiz fusion

---

### Post by Alex&amp;Linux on 2007-08-19
Same thing happens with Beryl too.
Im really ashamed about this, as I have been using beryl since March of this year, and have had, and resolved this issue no less than 4 times (this being about the fourth) :(
I should hope that most people resolve this, and not require more than mere common sense!
Thanks again for your time!

---

### Post by s_spiff on 2007-08-19
Probably the wrong thread to ask this but wanted to know can I use emerald with the default compiz that comes with Feisty? I have desktop effect [ which is basically compiz ] enabled, but want to do a little more by using emerald. So want to know can emerald be used with the default compiz and if yes, how do I go about it?

---

### Post by Alex&amp;Linux on 2007-08-19
Yep, shouldnt be a problem, after all, its just compiz. However, since it is only equipped with an "on or off" config manager, you would have to download some items to allow yourself to configure it (if im right, but check under "system -> preferences" for any compiz related material.

To look for more material, use Synaptic package manager.

In here, you'll probably just need "compiz-manager", but I could be wrong, as I have the fusion plugins, which require a few extra items as well as the barebones stuff.

Buena suerte!

---

### Post by Alex&amp;Linux on 2007-08-19
Oh, sorry, you could also try (provided that you have all the emerald packages)

Alt+F2
[HTML]emerald --replace[/HTML]

Which should place emerald over the standard GTK theme.

---

### Post by s_spiff on 2007-08-19
rocking. Wil try it out. but incase the emerald scrws up, how do I revert back?

---

### Post by realvz on 2007-08-19
why dont you get beryl....it is 100 times better than the default compiz in feisty....

---

