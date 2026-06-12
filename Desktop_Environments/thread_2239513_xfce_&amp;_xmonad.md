---
title: "xfce &amp; xmonad"
date: 2014-08-14
forum: Desktop Environments
---

### Post by Owain_Parry on 2014-08-14
Hey, I'm using Xubuntu 14.04, and I just downloaded and installed xmonad (I followed this: [http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE#Xfce_4.8.2C_Debian_Wheezy_7_Stable.2C_Xmonad_0.10.2C_May_2013](http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE#Xfce_4.8.2C_Debian_Wheezy_7_Stable.2C_Xmonad_0.10.2C_May_2013), section 5.3). It works fine, however when I log in all my xfce panels dissapear (they've visable for a moment, then they go). If I open panel settings I can create new ones and they're visable, but once I log out and log in again they all disappear. Any ideas on how I can fix this? Thanks.

New issue:
I've resolved my previous issue and now I'm having another one. For some reason, xmonad only seems to work properly if I start it with root privlages (i.e. 'sudo xmonad --replace'), but because I have created an entry for it as a startup application, I can't give it root privlages (there's nowhere to enter my password). This means every time I log on I have to manually open a terminal and type sudo xmonad --replace before I can start working. A minor inconvience but I'd rarther I didn't have to do that. On my Desktop (Debian 7.6), I don't have this issue, xmonad can be launched just fine from a standard user.

---

### Post by claracc on 2014-08-16
Please, don'use blue or violet colour in the font letter, is very hard to see.

I have found some links, which perhaps can be useful for your problem:

[http://www.haskell.org/haskellwiki/Xmonad/Frequently_asked_questions#Can_I_install_without_root_permission.3F](http://www.haskell.org/haskellwiki/Xmonad/Frequently_asked_questions#Can_I_install_without_root_permission.3F)

[http://xmonad.org/intro.html](http://xmonad.org/intro.html)

[http://xmonad.org/tour.html](http://xmonad.org/tour.html)

I hope it helps.

---

### Post by vasa1 on 2014-08-16
IMO, you'll have to figure out a way to stop XFCE's window manager from starting.

---

