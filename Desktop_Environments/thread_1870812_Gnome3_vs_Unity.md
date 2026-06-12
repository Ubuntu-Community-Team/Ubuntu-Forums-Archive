---
title: "Gnome3 vs Unity"
date: 2011-10-27
forum: Desktop Environments
---

### Post by Mazate on 2011-10-27
What is the easiest way to install the Gnome 3 desktop environment so that I can alternate between it and Unity?

---

### Post by typhoon_tip on 2011-10-27
I suppose you are running 11.10 :)

Open a terminal, then:
```
sudo apt-get install gnome-shell
```

Then you logoff, and click the "gear" icon, choose "GNOME" and then login, it will start with Gnome 3.

Note: if you have an ATI card, and you installed the proprietary driver, it will not work (well, it will be buggy, screen messed up). This is a known bug so, if you want to try it, you have to do so with stock ATI drivers with basic openGL 2D/3D capability, altough it may not work on newest cards.

---

### Post by markbl on 2011-10-28
Also, due to a ubuntu bug some of the unity global menu stuff disrupts gnome shell but you can fix this by typing the following command:

```

echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```

This will have no affect on Unity. Also add the webupd8team ppa to get the gnome-shell-extensions for gnome-tweak tool to customise your gnome-shell. See [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html).

---

### Post by weyland42 on 2011-10-28
> **markbl said:**
> Also, due to a ubuntu bug some of the unity global menu stuff disrupts gnome shell but you can fix this by typing the following command:

```

echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```This will have no affect on Unity. Also add the webupd8team ppa to get the gnome-shell-extensions for gnome-tweak tool to customise your gnome-shell. See [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html).
Since I upgraded to 11.10 the desktop environment experience seems to have descended into chaos. I find Unity unusable, and both Gnome and KDE have become unpredictable and unstable, not to mention extremely difficult / impossible to customise as before with 11.04.

So I looked at the link above, which looks like it might help. But it says "[COLOR=Red]**Important:** an user has reported that using the Alternative Status  Menu extension without having a profile picture crashes GNOME Shell. So  set a picture (under User Accounts) before installing this extension.[/COLOR]"

I'm using what 11.10 calls Gnome Classic now, and I can't find how to get at User Accounts. How do I set a picture?

---

### Post by weyland42 on 2011-10-28
I've now installed all the stuff mentioned in the link except the Alternative Menu potential problem. The result is worse than ever. Like a cross between Unity, Android, and some  computer game for masochists. Can't even navigate between windows without clicking Activities.

How can I get back to a nice clean and simple stable UI with all navigation, task bars, and workspace selectors at the bottom and nothing at the top?

If I can't, I'll just have to reinstall 11.04 (or some other Linux distro).

---

### Post by nilarimogard on 2011-10-28
> **weyland42 said:**
> Since I upgraded to 11.10 the desktop environment experience seems to have descended into chaos. I find Unity unusable, and both Gnome and KDE have become unpredictable and unstable, not to mention extremely difficult / impossible to customise as before with 11.04.

So I looked at the link above, which looks like it might help. But it says "[COLOR=Red]**Important:** an user has reported that using the Alternative Status  Menu extension without having a profile picture crashes GNOME Shell. So  set a picture (under User Accounts) before installing this extension.[/COLOR]"

I'm using what 11.10 calls Gnome Classic now, and I can't find how to get at User Accounts. How do I set a picture?

Actually I've fixed that bug by adding a delay before starting the extension. But it's better to be safe so if you want to set a profile picture, go to System Settings > User Accounts, click the "Unlock" button on the top right corner of the window and then you can set a picture for your account.

---

### Post by weyland42 on 2011-10-28
> **nilarimogard said:**
> Actually I've fixed that bug by adding a delay before starting the extension. But it's better to be safe so if you want to set a profile picture, go to System Settings > User Accounts, click the "Unlock" button on the top right corner of the window and then you can set a picture for your account.
Thanks, Nila, but I still can't see a way to set a picture . . .

[IMG]http://lh4.googleusercontent.com/-siUxM7NC_OI/Tqq4oCNJlII/AAAAAAAAICY/gk7T9DhGFYM/s912/_snapshot1.png[/IMG]

---

### Post by Mazate on 2011-10-28
Well, I hate to be a stick in the mud but Gnome 3 works fine for me.  I added it as per instructed and it works like a charm.  Yeah, it does have some limitations but I used to use it with Fedora and got used to it and grew to like it actually.  Seems to work fine on Ubuntu.

---

### Post by cbowman57 on 2011-10-28
Click here >>> [ATTACH]205673[/ATTACH]

---

