---
title: "Something lighter?"
date: 2008-01-02
forum: Desktop Environments
---

### Post by BBin on 2008-01-02
I have been using Ubuntu with gnome for a while now and I am satisfied with it, however it feels a little overkill for me since I only have a panel (100%transparent at tht top) with nothing more then the main menu and the gnome equivalent to windows' activity field on it, AWN as window minimise-bar or whatever i should call it and a mini-launcher panel in the bottom-rigt for amarok controls. I also have a pretty slow computer.

Screenshot:
[http://bayimg.com/naIBHaabl](http://bayimg.com/naIBHaabl)

I have done some thinking and I remember the first linux dist I ever tried was called "Damn small linux" and it had the main menu on the right-click on the desktop and I liked that so that leaves my Amarok-multimedia-buttons and the activity field on the panels for a future Desktop Environment.


I have a few things I am not willing to sacrifise:
Both QT(KDE) and GTK+ apps has to work since I use Amarok. All other programs are gtk+.
Conky system monitor
Avant WIndow Navigator
Emesene (latest msn protocol support)
Compiz-Fusion and Emerald theme manager + a lightweight (non-composited) alternative 
Some kind of one-click launcher (for my amarok controls)
Bluetooth easy accessing phones etc. support

I have looked at fluxbox and some other alternatives but I would like your input!
A configuration center that's better then gnomes would be a plus.

Thanks
//Robin

---

### Post by rickycodie on 2008-01-02
have you xfce? or maybe icewm?

---

### Post by urukrama on 2008-01-02
If you want to use Compiz-Fusion and Emerald, any of the other window managers are out of the question (you cannot have two window managers running). Xfce might be a good alternative then. Install it with:
> sudo aptitude install xfce4

It is lighter than Gnome, but still has all the things you want (including the option to use it with C-F and Emerald).

If you are willing to give up C-F and Emerald, I would suggest Openbox. It is light, looks nice and is easy to configure. You won't get a configuration window that is 'better' than Gnome. Openbox has the excellent Obconf, but it doesn't cover Gtk themes and icons. But these things are easy to do in other ways. Follow the link in my signature for more help.

You can use xcompmgr for some basic compositing (shadows, fading menus, acceleration, etc.) with window managers (Openbox, Fluxbox, Icewm etc). See [here]("http://ubuntuforums.org/showthread.php?t=75527") for more info.

---

### Post by ~LoKe on 2008-01-02
**EDIT**: Ah, didn't notice you require compiz.  Xfce is pretty much it. ;)

---

### Post by PeterJS on 2008-01-02
> **rickycodie said:**
> have you xfce? or maybe icewm?

Icewm doesn't play nice with compiz as far as I know, which is really too bad. Hopefully somebody will prove me wrong, I had a thread about it over in desktop customization, but got no response.

Oh, yeah and xfce is nice and does the right click on the desktop menu thing. Between the desktop menu and the compiz widget lay the only thing on my desktop is a small system tray, it's pretty easy to slim down.

---

### Post by ~LoKe on 2008-01-02
> **PeterJS said:**
> Icewm doesn't play nice with compiz as far as I know, which is really too bad. Hopefully somebody will prove me wrong, I had a thread about it over in desktop customization, but got no response.

Didn't even notice compiz was required for him.  Guess I can remove the Openbox suggestion. ;)

---

