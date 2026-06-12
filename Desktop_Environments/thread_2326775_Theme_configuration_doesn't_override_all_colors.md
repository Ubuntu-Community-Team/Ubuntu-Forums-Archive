---
title: "Theme configuration doesn't override all colors"
date: 2016-06-04
forum: Desktop Environments
---

### Post by chazzyfresh33 on 2016-06-04
I'm a big fan of the Numix theme, and I think with the desktop background I'm using it'll look really sharp with the "Xubuntu Blue" being used for the accents instead of the usual Orange. I've set this in the Theme Configuator and for the most part it works, however I've noticed that some apps don't seem to want to use this setting (examples, when selecting text in Firefox, but not Chrome, strangely, the sliders on the Theme Configurator menu, and the Software Updater). Is there anyway to make this setting more global?

---

### Post by Frogs Hair on 2016-06-04
The theme configuration application is very useful with some themes and does not work at all with others. There are blue variants of Numix available you might want try . Another option would be learn to modify the theme yourself.

---

### Post by chazzyfresh33 on 2016-06-04
Guess I'm not sure what I'm doing wrong then: per your suggestion, I looked up what colors I wanted to swap, found the gtkrc files in both gtk-2.0 and xfce-notify-4.0, changed every instance of them, and i'm still getting orange where there should be blue. same apps as well.

---

### Post by vasa1 on 2016-06-04
Are you on Ubuntu 16.04? If so, see if only gtk3 apps are not obliging.

---

### Post by chazzyfresh33 on 2016-06-04
I'm running Xubuntu 16.04, and ashamed to say that I don't really know how to tell the difference between Gtk3 and other apps. The XFCE menu has the color changes, as does Chrome, Thunderbird, File Manager, Writer, Calc, Pidgin, Terminal. Meanwhile, examples of the non working apps are Firefox, Software, Software Updater, Synaptic. I'm sorry if that's not helpful, please let me know if there's any other info that can help.

---

### Post by Dennis N on 2016-06-04
> I don't really know how to tell the difference between Gtk3 and other apps.

One way is to check which libgtk version the application depends on:

```
dmn@Kayleigh:~$ apt depends synaptic
synaptic
  Depends: libapt-inst2.0 (>= 0.8.16~exp12)
  Depends: libapt-pkg5.0 (>= 1.1~exp9)
  Depends: libc6 (>= 2.4)
  Depends: libept1.5.0
  Depends: libgcc1 (>= 1:4.2)
  Depends: libgdk-pixbuf2.0-0 (>= 2.22.0)
  Depends: libglib2.0-0 (>= 2.14.0)
  [COLOR="#FF0000"]Depends: libgtk-3-0 (>= 3.3.16)[/COLOR]
  Depends: libpango-1.0-0 (>= 1.14.0)
  Depends: libstdc++6 (>= 5.2)
  Depends: libvte-2.91-0
  Depends: libx11-6
  Depends: libxapian22v5
  Depends: hicolor-icon-theme

```

So, Synaptic Package manager uses the gtk 3 libraries and because of that, might be called a gtk 3 application.

---

### Post by chazzyfresh33 on 2016-06-04
Thanks for the tip. Near as I can tell yes, seems that only the GTK3 apps are being stubborn

---

### Post by Dennis N on 2016-06-04
You have a tough nut to crack trying to modify Numix. In the past, themes had a gtk.css file in the gtk-3.0 folder where you could change the color codes (many still do), but not the Numix in Xubuntu 16.04. Instead, that file contains a url linked to some resource file - part of the new way of doing things. It's getting too confusing for me to mess with. You might want to hunt down a blue version of Numix and go with that. I am trying Numix Arch Blue in Xubuntu 16.04 and it works well.

---

### Post by vasa1 on 2016-06-04
Try
```
apt-get remove -s libgtk-3-0 | grep Remv | cut -d ' ' -f 2
```
This is a harmless command because of "-s" (for simulation).

I'm puzzled by Calc and Writer. What versions are those? AFAICT, they should be gtk3 as well. Unless you haven't installed "libreoffice-gtk3". In which case they may run in gtk2 mode.

---

### Post by chazzyfresh33 on 2016-06-04
Numix Arch Blue definitely seems to be the way to go, and even gives me more of the dark mode which I like. Thanks for the tip, even if i don't like allowing software to beat me at something.
And yes, looks like my LibreOffice apps are all GTK 2

---

### Post by vasa1 on 2016-06-05
> **Dennis N said:**
> You have a tough nut to crack trying to modify Numix. In the past, themes had a gtk.css file in the gtk-3.0 folder where you could change the color codes (many still do), but not the Numix in Xubuntu 16.04. Instead, that file contains a url linked to some resource file - part of the new way of doing things. It's getting too confusing for me to mess with. You might want to hunt down a blue version of Numix and go with that. I am trying Numix Arch Blue in Xubuntu 16.04 and it works well.

@Dennis N, can you clarify whether LibreOffice is gtk3 on Xubuntu 16.04? OP mentions it being gtk2 which is hard to understand.

And do you have *libreoffice-gtk3* installed? Maybe it isn't present in Xubuntu 16.04 and needs to be installed if one wants proper integration with gtk3?

---

### Post by Dennis N on 2016-06-05
> Can you clarify whether LibreOffice is gtk3 on Xubuntu 16.04? OP mentions it being gtk2 which is hard to understand.

It doesn't depend on either libgtk-3-0 or libgtk2.0 

> do you have libreoffice-gtk3 installed?

No, it is not installed, but libreoffice-gtk is (but it's not a dependency). That makes it create the interface with gtk2, I assume. Is that correct?

---

### Post by vasa1 on 2016-06-05
> **Dennis N said:**
> It doesn't depend on either libgtk-3-0 or libgtk2.0 



No, it is not installed, but libreoffice-gtk is (but it's not a dependency). That makes it create the interface with gtk2, I assume. Is that correct?
This is what I see. To what extent that's because I upgraded from 14.04 to 16.04 or because I've installed Libreoffice via the fresh ppa (deb [http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu) xenial main), I can't say:```
07:45 PM ~ $ apt-cache rdepends libreoffice-gtk
libreoffice-gtk
Reverse Depends:
  libreoffice-core
  libreoffice-gnome
  libreoffice-gnome
  libreoffice-gnome
  xubuntu-desktop
  ubuntustudio-desktop
  libreoffice-core
  libreoffice-gnome
07:45 PM ~ $ apt-cache rdepends libreoffice-gtk3
libreoffice-gtk3
Reverse Depends:
  gir1.2-lokdocview-0.1
  gir1.2-lokdocview-0.1
07:45 PM ~ $ apt show libreoffice-gtk3
Package: libreoffice-gtk3
Version: 1:5.1.3-0ubuntu1
Priority: optional
Section: gnome
Source: libreoffice
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 862 kB
Depends: libreoffice-core (= 1:5.1.3-0ubuntu1), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.14), libcairo2 (>= 1.10.0), libgcc1 (>= 1:3.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.17.9), libpango-1.0-0 (>= 1.14.0), libstdc++6 (>= 5.2), libx11-6, uno-libs3 (>= 5.1.0~alpha), ure
Recommends: libreoffice-style-tango
Enhances: libreoffice
Homepage: http://www.libreoffice.org
Supported: 9m
Download-Size: 249 kB
APT-Manual-Installed: yes
APT-Sources: http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Description: office productivity suite -- GTK+ 3.0 integration

N: There is 1 additional record. Please use the '-a' switch to see it
07:46 PM ~ $ 

```
As you said, *libreoffice-gtk* helps libreoffice look decent with gtk2 themes; otherwise it looks very plain.

But if you have libreoffice-gtk3 installed, libreoffice will launch, by default, as a gtk3 application.

This is the version of libreoffice on my system:```
07:54 PM ~ $ apt-cache policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:5.1.3-0ubuntu1
  Version table:
     1:5.1.3-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     1:5.1.2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
07:55 PM ~ $ 

```
On my oldish laptop, I'm more comfortable with the gtk2 version and so I launch libreoffice calc, for example, using ```
SAL_USE_VCLPLUGIN=gtk libreoffice --calc
``` via the keyboard
or
```
Exec=bash -c 'SAL_USE_VCLPLUGIN=gtk libreoffice --calc %u'
``` via .desktop.

---

### Post by Dennis N on 2016-06-05
> But if you have libreoffice-gtk3 installed, libreoffice will launch, by default, as a gtk3 application.
I will test that. It is fine the way it is now, though.

Update: I added the libreoffice-gtk3 package, and in my opinion, the gtk2 theming looks better than the gtk3. System theme is Numix.

---

### Post by vasa1 on 2016-06-09
> **Dennis N said:**
> ...
Update: I added the libreoffice-gtk3 package, and in my opinion, the gtk2 theming looks better than the gtk3. System theme is Numix.
I missed your update!

For me, in gtk3 mode Adwaita and Greybird seem fine but both Ambiance and Numix don't show the lettering of the *File, Edit, View, etc* menu bar clearly!

---

### Post by Dennis N on 2016-06-09
> **vasa1 said:**
> I missed your update!

For me, in gtk3 mode Adwaita and Greybird seem fine but both Ambiance and Numix don't show the lettering of the *File, Edit, View, etc* menu bar clearly!

All clear here. I have a Firefox theme (persona) installed that changes the background of the menu bar and tool bars. That can make a difference. Tools > Options > Personalization > Own Theme. Specifically, I use a theme called "Gray and white Gradient" (by Cessar69).

---

### Post by vasa1 on 2016-06-09
> **Dennis N said:**
> All clear here. I have a Firefox theme (persona) installed that changes the background of the menu bar and tool bars. That can make a difference. Tools > Options > Personalization > Own Theme. Specifically, I use a theme called "Gray and white Gradient" (by Cessar69).
Yes, I remember you mentioning that. But could you please temporarily disable the theme (in gtk3 mode) just to see how Ambiance & Numix behave as far as the menu bar goes? If it's not just me, I'm wondering why there aren't more posts on the topic ...

---

### Post by Dennis N on 2016-06-09
> **vasa1 said:**
> could you please temporarily disable the theme (in gtk3 mode) just to see how Ambiance & Numix behave as far as the menu bar goes?

Happy to oblige. It is interesting to see the differences. Three screenshots of the menu bar area:

1) L.O. writer + numix + gtk2 and no persona
2) L.O. writer + numix + gtk3 and no persona
3) L.O. writer + numix + gtk3 with persona

Adding the persona (firefox mini-theme) makes the gtk3 usable.
Not shown: gtk2 with persona, which I use, and looks the best.

P.S. - there is no ambiance theme in Xubuntu, so I can't look at that.

---

### Post by vasa1 on 2016-06-10
Thanks for taking the time and trouble to check!

So, as far as Numix goes, it's not just me which is a relief. 

Things are a bit hectic for me but I suppose I could visit the github page of Numix and post an issue if one hasn't been posted already.

Re. the persona, I've tweaked Greybird itself a bit to get it as grey as I like nearly everywhere but without any gradient; it maybe possible but my css (or gtkrc) skills aren't up to that.

As for Ambiance, even Lubuntu doesn't ship with it so I installed "light-themes" and that got me Ambiance and Radiance, along with a few dependencies.

---

### Post by Dennis N on 2016-06-10
What is the advantage of our using the libreoffice-gtk3 package? It appears the problems here can be avoided by sticking with gtk2. That seems like the best option to me.

---

### Post by vasa1 on 2016-06-10
> **Dennis N said:**
> What is the advantage of our using the libreoffice-gtk3 package? It appears the problems here can be avoided by sticking with gtk2. That seems like the best option to me.
As of now, there's absolutely no advantage that I can see. The only issue is that at some point they may pull the plug on gtk2.

I have practical issues when running LibreOffice in gtk3 mode on my oldish laptop. I made this thread some weeks ago:  [LibreOffice Writer 5.1.2: please test this]("http://ubuntuforums.org/showthread.php?t=2324762"). The impression I got from the responses is that gtk3 is fine with newer hardware.

---

