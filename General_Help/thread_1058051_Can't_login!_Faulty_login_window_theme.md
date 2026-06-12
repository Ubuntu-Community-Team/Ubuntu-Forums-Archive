---
title: "Can't login! Faulty login window theme"
date: 2009-02-02
forum: General Help
---

### Post by Photoguy on 2009-02-02
Ok, I've searched all over, and asked on the IRC channel, now I think I can safely bother you all with a thread.


I installed a new theme login window theme (from gnome-look) 
So I logged off, now when I boot up it stops at the login screen, but doesn't fully load it.
All I can see is the background image, and the "wait cursor" which is spinning.

Is there a way to remove/choose different (login window) theme, 
through the terminal?
Because I can't even log in at all.

I would appreciate some help.

-Photoguy-

---

### Post by khelben1979 on 2009-02-02
You have 2 window managers called: KDM (uses KDE) and GDM (uses Gnome) and if you know which one of these which is used at the present you can configure to only use KDM instead of GDM or the other way around.

If GDM is messed up, the KDM will be used from now on.

sudo apt-get install kdm

---

### Post by Photoguy on 2009-02-02
Thank you very much, I was able to log in!
is there a way to switch between kde and gnome in the terminal?
Just in case this happens again.

---

### Post by khelben1979 on 2009-02-02
If you use the GDM for login I know you have the possibility to choose if you want to start a Gnome or KDE session, if, both desktop enviroments are installed.

With KDM I don't know at the present. From my old personal experience I wasn't able to start the Gnome desktop if I chose KDM is login manager, but this doesn't mean it's the case nowadays.

Nice to hear that it works better now. :-)

---

