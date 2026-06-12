---
title: "Is it possible to change my Gnome desktop to KDE?"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by mikledet on 2007-06-12
I want to try thr KDE desktop, but I've already installed Ubuntu instead of Kubuntu, is it possible to switch from Gnome to KDE?  If so, can you please explain howto..?
Oh, and one more thing, if I change, does it mess up beryl or that stays the same?  Thanks

---

### Post by timcredible on 2007-06-12
should be able to just install the kde package from synaptic, and then choose kde as your desktop in the 'options' from the login screen.  your video drivers won't be affected, but you'll need to start beryl in kde (probably just put 'beryl-manager' in .kde/Autostart, but do a search on that).

gnome and kde will coexist happily, so it's easy to install both and go back and forth between them, they're just window managers.  you could also install xfce and fluxbox if you want.

---

### Post by mikledet on 2007-06-12
Thanks for that reply, but could you please elaborate a little more as to where/how I download and install KDE and then set it?  (I'm a little too much of a n00b to figure it all out myself)

---

### Post by DrRootabega on 2007-06-12
On the top Panel go to : System->Administration->Synaptic Package Manager.  Then search for "kde-core" and mark that package for installation by right clicking on it.  You can set your system to boot with KDE when you login.  There should be a menu somewhere where you can secect which desktop environments you have installed.

---

### Post by mikledet on 2007-06-12
In the Synaptic manager there are many KDE packages, I need to install only the kde-core one?  Also, does it install it by itself?  and once I have it installed, how do I switch to KDE.

---

### Post by pwaldo on 2007-06-12
> **mikledet said:**
> In the Synaptic manager there are many KDE packages, I need to install only the kde-core one?  Also, does it install it by itself?  and once I have it installed, how do I switch to KDE.
To install KDE, execute this:

```
sudo apt-get install kde
```
For what you want to do, I think that kde is the appropriate package.

As far as using KDE vs. GNOME, log out of your session so you are presented with the login screen again.  There should be something that allows you to select your session-type.  Select KDE.  

HTH!

---

### Post by arbulus on 2007-06-12
I did it this way.  In the terminal, type:

```
sudo apt-get install kubuntu-desktop
```

Log out.  
Then, at your login screen, click "Sessions", and you should see KDE as a choice.  Click that and then continue with your login.

---

