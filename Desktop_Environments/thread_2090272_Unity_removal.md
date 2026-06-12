---
title: "Unity removal"
date: 2012-12-01
forum: Desktop Environments
---

### Post by zvacet on 2012-12-01
Is it possible to complete and safe remove unity from 12.10?

---

### Post by cwsnyder on 2012-12-01
Two ways I know of:

1) Install the server edition, no GUI, just CLI.

2) Replace Unity with one of the alternative desktops, ie. KDE, GNOME, Xfce, LXDE, E17, Awesome WM, WindowMaker, Fluxbox, Blackbox, Openbox, jwm, IceWM, fvwm, flwm, or others.

---

### Post by zvacet on 2012-12-02
I know that,but I was asking is it same as in 12.04.Like this

```
sudo apt-get remove unity unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files unity-lens-music unity-lens-applications gir1.2-unity-5.0 unity-common indicator-sound indicator-power indicator-appmenu libindicator7 indicator-application indicator-datetime indicator-messages libnux-2.0-0 nux-tools libunity-misc4 unity-2d-common
```

---

### Post by MG&amp;TL on 2012-12-02
That won't remove anything vital. Just make sure you have another DE installed first. And I wouldn't run that from inside unity. :)

---

### Post by zvacet on 2012-12-02
> That won't remove anything vital. Just make sure you have another DE installed first. And I wouldn't run that from inside unity. 

Good to know it won´t remove vital things.I planed to install another DE first,and then remove Unity.I´m asking because I don´t want to get in trouble.I think your answer is good enough to avoid that.I will post you when I do the changes.I hope you will not [IMG]http://www.cosgan.de/images/smilie/frech/o080.gif[/IMG]

---

### Post by kurt18947 on 2012-12-02
Would installing the gnome version of 12.10 work for you?  If you're trying to avoid the Gnome 3 vibe entirely that won't work, obviously.

---

### Post by zvacet on 2012-12-02
My intention is to install Xubuntu and remove Unity.I don´t know if this operation will remove some part of Gnome or not.That is why I think MG&TL advice is good.Any ideas,suggestions?I don´t want to reinstall and install Xubuntu that way.Beside if I don´t want to use Xubuntu I want to be sure I can come back to unity.In the past it was secure way of doing this kind of stuff,but now on same site you have warnings when you want to do this.Read [this.]("http://www.psychocats.net/ubuntu/purexubuntu")

---

### Post by Bucky Ball on 2012-12-02
If you want just the desktop environment (rather than the full Xubuntu) you only need to install xfce4 which can be found in Software Centre or Synaptics or you can install with:

```
sudo apt-get install xfce4

```... then log out, choose from Sessions pop-up, log in so you are in xfce4 *then* remove Unity. ;)

If you are looking for the full install, xubuntu-desktop will do that but be warned your menus will now contain everything (default apps, etc) from the regular Ubuntu *and* Xubuntu. It can get crowded and confusing. This won't happen if just installing xfce4.

---

### Post by zvacet on 2012-12-02
>  xubuntu-desktop will do that but be warned your menus will now contain everything (default apps, etc) from the regular Ubuntu and Xubuntu. It can get crowded and confusing. This won't happen if just installing xfce4.

That is one of reasons I wanted to remove unity in first place.I followed your advice and install just xfce-4 and so far so good.Tnx! [IMG]http://www.cosgan.de/images/smilie/froehlich/k010.gif[/IMG]

---

### Post by Krytarik on 2012-12-02
> **zvacet said:**
> That is one of reasons I wanted to remove unity in first place.
Unity is just a desktop shell, removing it would remove only *one* of the default 'applications' of the regular "Ubuntu" installation: itself. :P

Personally, especially since you indicated you might want to return to Unity, I'd just either leave it alone entirely, or at max hide it from the session options on login screen by adding...
```
Hidden=True
```...to its session .desktop file "/usr/share/xsessions/ubuntu.desktop", since it doesn't really take up that much space that it's worth risking screwing up the entire installation. ;-)

Regards.

---

### Post by zvacet on 2012-12-02
@ **Krytarik**

Tank you for your suggestion,but reason why i started this thread is that I don´t want Ubuntu apps to show in Xubuntu installation as **Bucky Ball** said.I have to say that I installed only **xfce4**,but I still see some Ubuntu apps.Never mind.It is not perfect,but it is working.Now it is time to play with Xfce. :)

---

### Post by Bucky Ball on 2012-12-02
That is what is being said. Removing Unity only removes that desktop environment, NOT any default Ubuntu apps. Like removing xfce4. If you have only installed xfce4 the apps will be Ubuntu apps, NOT Xubuntu. Xfce4 doesn't install any. 

The only way you will get the Xubuntu default apps is to install xubuntu-desktop, then you will have both. To ONLY have xubuntu default apps and no Ubuntu remnants, you may as well just install Xubuntu ...

---

### Post by zvacet on 2012-12-03
>  To ONLY have xubuntu default apps and no Ubuntu remnants, you may as well just install Xubuntu ...

That was thing I wanted to avoid.Finally I installed xubuntu-desktop and now I have complete Xfce experience.O.K I still see ubuntu apps,but nobody´s perfect!Tank you for your advices and replays!

---

### Post by Bucky Ball on 2012-12-03
No probs. Enjoy. Xfce rocks! But now I'm repeating myself ... lol ;)

My desktop is a total hybrid. I started by installing Ubuntu Studio and then added xubuntu-desktop, ubuntu-desktop, edubuntu and Ubuntu Satanic artwork and other things I don't remember! It developed over a few years but probably needs a complete reinstall to be honest ...

---

