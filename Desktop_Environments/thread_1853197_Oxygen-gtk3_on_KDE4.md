---
title: "Oxygen-gtk3 on KDE4"
date: 2011-10-01
forum: Desktop Environments
---

### Post by TuxIsAwesome on 2011-10-01
I am currently running Oneric Ocelot, and I quite frankly think that this is the best release of Ubuntu so for, even for a beta it exceeds my stability expectations.

I am having one issue though. All of my Gtk3 apps look fugly as ell in KDE4. I've checked to make sure that I have a symlinked .config/gtk-3.0 and a settings.ini file inside of it. Everything should theoretically work, but it doesn't. I get that aweful Windows-98 Esque fallback theme. The /local/share/themes/oxygen-gtk folder also contains a gtk3.0 folder and the GTK3 engines for oxygen-gtk are also installed.

[Settings] 
# DO NOT EDIT! This file will be overwritten by LXAppearance.
# Any customization should be done in ~/.gtkrc-2.0.mine instead.

gtk-theme-name="oxygen-gtk"
gtk-fallback-theme-name="oxygen-gtk"
gtk-icon-theme-name="Faenza-Cupertino"
gtk-font-name="Cantarell 9"
gtk-cursor-theme-name="DMZ-Black"
gtk-cursor-theme-size=0
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-toolbar-icon-size=GTK_ICON_SIZE_LARGE_TOOLBAR
gtk-button-images=0
gtk-menu-images=1
gtk-enable-event-sounds=1
gtk-enable-input-feedback-sounds=1
gtk-xft-antialias=1
gtk-xft-hinting=1
gtk-xft-hintstyle="hintfull"
gtk-xft-rgba="rgb"
include "/home/namehidden/.gtkrc-2.0.mine"

---

### Post by elnur on 2011-10-22
Yea, I'd like to know how to make GTK3 apps look as good as GTK2, too.

---

### Post by Aide9aic on 2011-10-25
Reported in bug #852858, "[Please package oxygen-gtk3]("https://bugs.launchpad.net/ubuntu/+bug/825858")."

You can find it in two PPAs at the moment:
[LIST]
[*][šumski's KDE Goodies]("https://launchpad.net/~hrvojes/+archive/kde-goodies")
[*][Bellegarde Cedric's PPA]("https://launchpad.net/~gnumdk/+archive/ppa")
[/LIST]

---

### Post by schnelle on 2011-10-25
I made HOWTO thread on kubuntuforums: [http://kubuntuforums.net/forums/index.php?topic=3118994.0](http://kubuntuforums.net/forums/index.php?topic=3118994.0)

---

### Post by elnur on 2011-10-25
> **schnelle said:**
> I made HOWTO thread on kubuntuforums: [http://kubuntuforums.net/forums/index.php?topic=3118994.0](http://kubuntuforums.net/forums/index.php?topic=3118994.0)

That worked great. Thanks, man!

Now I need to setup GTK3 fonts. If it's possible, I'd like it to use the same font settings as KDE apps do, but if I need to do it manually, fine. Any ideas?

---

### Post by schnelle on 2011-10-25
All my gtk2 and gtk3 apps use (default) ubuntu font. Look at System Settings> Application appearance> GTK+ appearance

---

### Post by elnur on 2011-10-25
> **schnelle said:**
> All my gtk2 and gtk3 apps use (default) ubuntu font. Look at System Settings> Application appearance> GTK+ appearance

Font family is okay, but not the size. For example, Gnome Calculator picks up the right font size:

[IMG]http://imagepaste.nullnetwork.net/img/1319536430calc.png[/IMG]

But Evince does not:

[IMG]http://imagepaste.nullnetwork.net/img/1319536456evince.png[/IMG]

---

### Post by DZ* on 2011-10-26
> **schnelle said:**
> I made HOWTO thread on kubuntuforums: [http://kubuntuforums.net/forums/index.php?topic=3118994.0](http://kubuntuforums.net/forums/index.php?topic=3118994.0)

It does look pretty but evolution's pane where email subjects are listed becomes "invisible". It comes up as an empty rectangle. When I remove gtk3-engines-oxygen, it all comes back ... looking ugly as ever.

---

### Post by bdw on 2011-11-07
It appears that gtkpod will segfault when gtk3-oxygen is set as the gtk3 theme.  Synaptic will start up but the menus won't work.

---

### Post by DDZ on 2012-01-04
> **DZ* said:**
> It does look pretty but evolution's pane where email subjects are listed becomes "invisible". It comes up as an empty rectangle. When I remove gtk3-engines-oxygen, it all comes back ... looking ugly as ever.
[SIZE="3"][FONT="Times New Roman"]The same thing happened to me this afternoon (Evolution 3.2.1).
Any idea to solve the problem ? Any way to contact the developper in order to indicate the bug ?

Thank you in advance for your answer ![/FONT][/SIZE]

---

### Post by philippe44 on 2012-01-22
> **DDZ said:**
> [SIZE="3"][FONT="Times New Roman"]The same thing happened to me this afternoon (Evolution 3.2.1).
Any idea to solve the problem ? Any way to contact the developper in order to indicate the bug ?

Thank you in advance for your answer ![/FONT][/SIZE]

Used to have the same problem. I downloaded oxygen-gtk3 source and rebuild it but what solved the problem was to install GTK configuration from here 
[http://packages.netrunner-os.com/pool/main/k/kde-gtk-config/kde-gtk-config_1.0.1~svn812a8445_i386.deb](http://packages.netrunner-os.com/pool/main/k/kde-gtk-config/kde-gtk-config_1.0.1~svn812a8445_i386.deb)
And then set various parameters (in the system panel, with other usual GTK stuff). Evolution now working fine. Seems like some parameters where not set in my .config/gtk-3.0/settings.ini and that was causing the issue. I don't think that the rebuild of the oxygen-gtk3 was the solution, but told you just in case

---

### Post by Pug226 on 2012-01-29
Running gnome-settings-daemon fixed the GTK appearance for me. Open a terminal, run your GTK app (synaptic, evolution, etc.), and then run ```
gnome-settings-daemon
```The appearance instantly changes. Kill gnome-settings-daemon and the appearance reverts back to the ugly style. Now I just need to start this upon log in.

I tried the gtk3 engine hack but it didn't work. Also, it bit back when the 3rd party repository ([https://launchpad.net/~gnumdk/+archive/ppa](https://launchpad.net/~gnumdk/+archive/ppa)) upgraded to KDE 4.8; Oneiric is using KDE 4.7.

Packages installed:
[FONT="Courier New"]appmenu-gtk3                 0.3.0-0ubuntu1
gtk3-engines-unico           1.0.1-0ubuntu1
ibus-gtk3                    1.3.99.20110419-1ubuntu3
libavahi-ui-gtk3-0           0.6.30-4ubuntu1
libcanberra-gtk3-0           0.28-0ubuntu11
libcanberra-gtk3-module      0.28-0ubuntu11
libdbusmenu-gtk3             0.4.3-0ubuntu4
libdbusmenu-gtk3-4           0.5.0-0ubuntu3
libindicate-gtk3             0.6.1-0ubuntu1
libmoonlight-gtk3.0-cil      2.3-0ubuntu5
libseed-gtk3-0               3.2.0-0ubuntu1
python-aptdaemon.gtk3widgets 0.43+bzr697-0ubuntu1
kde-config-gtk               2:0.5.3-1ubuntu2
gtk2-engines-oxygen          1.1.2-1ubuntu1[/FONT]

---

### Post by SnappyU on 2012-02-07
The kubuntu forums link is [http://www.kubuntuforums.net/showthread.php?55792-HOWTO-gtk3-engines-oxygen-for-gtk3-apps&](http://www.kubuntuforums.net/showthread.php?55792-HOWTO-gtk3-engines-oxygen-for-gtk3-apps&)

---

