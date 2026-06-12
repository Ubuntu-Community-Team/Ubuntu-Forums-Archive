---
title: "XMonad slower to start than gnome"
date: 2009-11-07
forum: Desktop Environments
---

### Post by khingebjerg on 2009-11-07
Hi.

I recently installed Ubuntu 9.10, and when i launch XMonad from gdm it takes much longer to start than gnome, and I find that a little strange. Have anybody else experienced this, and can I do anything to speed it up?

Oh, and it's the same in XUbuntu 9.10, which I'm running now, except that now of course it is XFCE that starts faster than XMonad.

/khingebjerg

---

### Post by semperfizh on 2009-12-07
Indeed, that is true, if you start your session by choosing XMonad.
However if you start XMonad within gnome session, then you 
dont notice any difference in boot time.

Just a note: As far as I know Gnome is not a window manager, metacity is the one
which runs by default. Running XMonad, you replace metacity and not necessarily
gnome. 

Cheers

---

### Post by akashiraffee on 2009-12-07
> **semperfizh said:**
> 
Just a note: As far as I know Gnome is not a window manager, metacity is the one
which runs by default. Running XMonad, you replace metacity and not necessarily
gnome. 


Yo, totally correct.  You should not run XMonad in Gnome, you should run it INSTEAD of gnome or XFCE.

Unless you want to do it this way:
[http://haskell.org/haskellwikiXmonadUsing_xmonad_in_Gnome#Starting_GNOME_with_xmonad](http://haskell.org/haskellwikiXmonadUsing_xmonad_in_Gnome#Starting_GNOME_with_xmonad)

eg:
> 
Overall most people on a variety of distros seem to get best results by using an applications/xmonad.desktop file and telling gnome to use xmonad instead of metacity by running: 
**gconftool-2 -s /desktop/gnome/session/required_components/windowmanager xmonad --type string **
For xmonad to start automatically on login you need an applications/xmonad.desktop file on your system. If your distro doesn't provide it, create the following file:

If you do this any other way you will just be screwing stuff up.

---

### Post by semperfizh on 2009-12-07
> **akashiraffee said:**
> Yo, totally correct.  You should not run XMonad in Gnome, you should run it INSTEAD of gnome or XFCE.

Unless you want to do it this way:
[http://haskell.org/haskellwikiXmonadUsing_xmonad_in_Gnome#Starting_GNOME_with_xmonad](http://haskell.org/haskellwikiXmonadUsing_xmonad_in_Gnome#Starting_GNOME_with_xmonad)

eg:


If you do this any other way you will just be screwing stuff up.

Actually, I found a method running XMonad within Gnome and 
all works great! (I did not follow haskell.org recommendation, which indeed
screws things up.)
Now it is for me like using Gnomes
advantages with a beautiful tiling window manager. PS. import module "XMonad.Config.Gnome" in your ~/.xmoand/xmonad.hs ;)

---

### Post by akashiraffee on 2009-12-07
Well, that's cool then, as long as you know what you are doing.   

This is the first real world app I've ever seen written in Haskell.  Apparently it is making a comeback! :p

---

### Post by semperfizh on 2009-12-07
> **akashiraffee said:**
> Well, that's cool then, as long as you know what you are doing.   

This is the first real world app I've ever seen written in Haskell.  Apparently it is making a comeback! :p


It has always been there... hehe ;). Anyway, ubuntu should definitely take
tiling windows as an option into its new releases. Why do we always have to hack
for the cool things!?

---

