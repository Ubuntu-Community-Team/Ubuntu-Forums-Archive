---
title: "Installing GNOME Classic"
date: 2012-05-30
forum: Desktop Environments
---

### Post by piriton on 2012-05-30
Hi,

I am becoming frustrated with Unity and would like to install gnome-classic on 12.04.

I understand that GNOME Classic is sometimes called GNOME Fallback.

How can I do that ?  Is there a .deb within the main repositories, that I can install with apt-get ?

---

### Post by traditionalist on 2012-05-30
> **piriton said:**
> Hi,

I am becoming frustrated with Unity and would like to install gnome-classic on 12.04.

I understand that GNOME Classic is sometimes called GNOME Fallback.

How can I do that ?  Is there a .deb within the main repositories, that I can install with apt-get ?

Ubuntu Software Centre;

[[IMG]http://img803.imageshack.us/img803/5829/selection001q.th.png[/IMG]](http://img803.imageshack.us/i/selection001q.png/)

[[IMG]http://img818.imageshack.us/img818/6232/selection001ll.th.png[/IMG]]("http://img818.imageshack.us/i/selection001ll.png/")

---

### Post by piriton on 2012-05-30
Cool.  What is the main package, which should be installed.

```

# apt-get install <gnome-something ? >

```

---

### Post by traditionalist on 2012-05-30
> **piriton said:**
> Cool.  What is the main package, which should be installed.

```

# apt-get install <gnome-something ? >

```

You can get it from the developer site as well;

[https://live.gnome.org/GnomeShell](https://live.gnome.org/GnomeShell)

---

### Post by Cheesemill on 2012-05-30
```
sudo apt-get install gnome-panel
```

For more info see this post:
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by piriton on 2012-05-30
Works a charm and thanks for the link, very useful !

---

### Post by Rallg on 2012-05-30
My first experience with Unity was frustration, but after awhile I like it better than gnome-classic. Here are some tips to help (since you'll still be able to log-in to unity, even afer installing gnome-classic):

1. If your Unity menu is too cluttered, you can use gnome-classic's System Tools - Preferences - Main Menu to add or remove many of the launchers. Note that some, such as the workspace switcher, seem to be non-removable from the unity launcher.

2. Consider making the unity launcher appear or disappear when you mouse-over the left edge of your screen. unity's System Settings - Appearance - behavior tab. Auto-Hide on, left edge (corner didn't work for me), try high sensitivity first. If the sensitivity is too low, then you have to really bonk the mouse to the edge (rapid approach, maybe even slide it along the edge) before the unity menu appears).

3. There is a PPA (private repository, not part of the Ubuntu distribution) that has a ClassicMenu Indicator application. Find it on the Internet. What it does is place a small icon in the top unity taskbar. Mouse over the icon, and a classic-like menu appears.

The reason I've begun to like unity is that I have a netbook. When configured to my taste, unity takes up less screen area than does gnome-classic.

---

### Post by ubuntu27 on 2012-05-30
To install Gnome Fallack or "gnome classic"

```
[sudo apt-get install gnome-session-fallback]("apt://gnome-session-fallback")
```


You can choose which session and desktop environment you want in the login screen.

---

### Post by Rallg on 2012-05-30
After installing the fallback, you must log out (or reboot) then log back in, for it to take effect. When you get to Ubuntu's login screen, look just above at to the right of where you enter your user name and password. You'll see a little circular Ubuntu icon. Click it, and you'll get a menu of alternatives. The rest is self-explanatory.

If you do choose Gnome, then you can revert to Unity by the same method, the next time you log in. There may or may not be a way to do it dynamically while you are logged in; I wouldn't try it.

---

### Post by piriton on 2012-05-30
In the end I gave up with GNOME Fallback and Unity and installed KDE (apt-get install kubuntu-desktop) and rebooted.  I assume that kubuntu-desktop is the same as kde-plasma-desktop.

---

### Post by overcast on 2012-05-30
You can also get [appmenu]("http://slashstack.com/297/how-to-install-gnome-classic-appmenu-indicator-on-unity") in unity, just in case that is the only thing you need in unity or miss about gnome classic.

---

