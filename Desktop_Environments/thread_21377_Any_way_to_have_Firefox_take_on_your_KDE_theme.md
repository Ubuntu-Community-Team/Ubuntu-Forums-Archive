---
title: "Any way to have Firefox take on your KDE theme?"
date: 2005-03-21
forum: Desktop Environments
---

### Post by dermotti on 2005-03-21
Anyone know if there is a way to get firefox to follow the KDE theme you specify? So far it only takes on the window decoration.

---

### Post by poofyhairguy on 2005-03-21
[QUOTE=dermotti]Anyone know if there is a way to get firefox to follow the KDE theme you specify? So far it only takes on the window decoration.[/QUOTE]


Good question....I wish I knew...

This is a problem I have as well..

---

### Post by wbeck85 on 2005-03-21
Not directly. Firefix is not currently incorporated into KDE. There are people who are working on that, though i dont know of any one specifically. However, you can download different themes from [https://addons.mozilla.org/themes/?application=firefox](https://addons.mozilla.org/themes/?application=firefox)

There is a plastik theme that looks pretty good. Enjoy

---

### Post by bushsux on 2005-03-21
[QUOTE=dermotti]Anyone know if there is a way to get firefox to follow the KDE theme you specify? So far it only takes on the window decoration.[/QUOTE]

Using gtk2-engines-gtk-qt is the easiest way but it is not 100% and can crash some gtk programs. Works for firefox and gaim for me though.

---

### Post by dermotti on 2005-03-21
Is that something i download? heheh

---

### Post by bobmitch on 2005-03-22
Why not just use the Pimpzilla theme for firefox?

Pimpzilla > Any Gnome/Metacity theme.  ;)

---

### Post by Ironi on 2005-03-22
[QUOTE=bobmitch]Why not just use the Pimpzilla theme for firefox?

Pimpzilla > Any Gnome/Metacity theme.  ;)[/QUOTE]
Argh, now look what I went and did after viewing a [PimpZilla screenshot](http://people.zeelandnet.nl/marco/pimpzilla/images/pimpzilla.jpg)... I blame *you* for this. ;)

[[img]http://img182.exs.cx/img182/8420/ss200503224ky.th.png[/img]](http://img182.exs.cx/img182/8420/ss200503224ky.png)

---

### Post by Julius on 2005-03-22
If you have Gnome installed, login to it and change the font preferences or whatever you want 
Then go back to Kde, and run "gnome-settings-daemon". Font configuration will be taken from Gnome, and the colours will be taken from Kde (for firefox you can theme that fits better with kde if you don't like how it looks) . So they will look fine ;)

If you don't have gnome installed I guess you'll have to install gtk2-engines-gtk-qt.

---

### Post by lao_V on 2005-03-22
If you want a KDE integrated browser then might as well use konqueror. It is just as good in my opinion (for normal browsing anyway)

---

### Post by apokryphos on 2005-03-22
As mentioned above, the package you want is the gtk2-engines-gtk-qt package; it's in the repositories. From there, go into your kcontrol and under Appearance & Themes you should have GTK Styles and Fonts.

However, I would recommend Konqueror myself; I find it much faster (both starting up and loading pages); partly because of the KDE integration.

---

### Post by lao_V on 2005-03-22
Have a look at the [features]("http://www.konqueror.org/features/browser.php") of konqueror. You will find that it does almost everything that Firefox does. If I'm not mistaken, both of them are based on the Mozilla code??

---

### Post by apokryphos on 2005-03-22
[QUOTE=lao_V]Have a look at the [features]("http://www.konqueror.org/features/browser.php") of konqueror. You will find that it does almost everything that Firefox does. If I'm not mistaken, both of them are based on the Mozilla code??[/QUOTE]
Hmm, not quite. Mozilla/Firefox uses the Gecko engine; Konqueror uses KHTML (which Safari has now adopted, too).

---

### Post by bobmitch on 2005-03-22
> **Ironi]Argh, now look what I went and did after viewing a [PimpZilla screenshot](http://people.zeelandnet.nl/marco/pimpzilla/images/pimpzilla.jpg)... I blame *you* for this.  said:**
> [img]http://img182.exs.cx/img182/8420/ss200503224ky.th.png[/img][/url]

All that's missing is a leapordskin wallpaper... :D

---

### Post by dermotti on 2005-03-22
I dont know why, but my Konquerer web browser is WAY slower than firefox.

---

### Post by bored2k on 2005-03-22
[QUOTE=dermotti]I dont know why, but my Konquerer web browser is WAY slower than firefox.[/QUOTE]
 I was pretty amazed when I didn't see a trace of Firefox on Kubuntu.
I wouldn't leave firefox for konqueror at all .

---

### Post by Ironi on 2005-03-23
Konqueror doesn't seem to be too much slower than Firefox here. I don't really use it too much as a web browser, though. I miss a few features that Firefox has -- most notably the middle-mouse autoscroll. #-o

---

### Post by apokryphos on 2005-03-23
> **dermotti]I dont know why, but my Konquerer web browser is WAY slower than firefox.[/QUOTE]
You should look into that said:**
>  I was pretty amazed when I didn't see a trace of Firefox on Kubuntu.
Well, it is a *kde*-based distro; I doubt kubuntu is going to want to have all the GTK stuff there. Especially when there's a decent kde-equivalent (and superior one, IMO) around. 
> I wouldn't leave firefox for konqueror at all .
Whatever blows your hair back. ;)
[quote=Ironi]I miss a few features that Firefox has -- most notably the middle-mouse autoscroll.[/quote]
Why not drop it as a feature suggestion on bugs.kde.org?

---

### Post by Ironi on 2005-03-23
[QUOTE=apokryphos]Why not drop it as a feature suggestion on bugs.kde.org?[/QUOTE]
I would, but it turns out that [it's already implemented]("http://bugs.kde.org/show_bug.cgi?id=97367"). I just had to uncheck "Middle click opens URL in selection" under Web Behavior. I don't like it as much as Firefox's, though; it's not variable-speed and it completely disables middle-mouse paste in the viewing area (Firefox still lets you do that: middle click, move a bit off the arrows, and mclick again).

Konqueror also isn't as easily extensible as Firefox is, AFAICT. Plugin support is there, but there's a reason why developers prefer Firefox's extension system over plugins.

Firefox simply has too much momentum for me to switch away completely. Konqueror is a better browser than vanilla Firefox, but add in extensions and customization and there is no contest -- Firefox wins. I <3 adblock, webdeveloper, compactmenus, ...

---

### Post by apokryphos on 2005-03-23
Customization in Konqueror is great. GTK engine for fonts in kcontrol has made gtk apps slightly more bearable, but the tight kde integration with Konqueror is a big plus for me; speed is another such thing. Firefox has a few great points; it's assuredly a very decent browser (the growth in use speaks for itself). I'm not telling you to switch away completely; anyone can use whatever browser they please.

---

