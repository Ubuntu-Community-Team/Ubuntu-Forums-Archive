---
title: "gtk apps in kde considered harmful (to the eye)"
date: 2010-01-25
forum: Desktop Environments
---

### Post by ciuci on 2010-01-25
qt apps that just use qt and not kdelibs look perfect by default in gnome, and kde apps also can be set to&#65279; look really good in gnome in the system settings appearance dialog, but there is no real integration with gtk apps in kde. i mean both suse and kubuntu use the same qtcurve theme that makes gtk look kind of like qt but not really. i find it really ugly! first of all it's missing the cool gradient oxygen has that matches the gradient in the titlebar (mostly visible if you disable those stripes) and also all the widgets are obivously different, and ugly! (i don't mean desktop widgets, i mean the buttons and comboboxes and etc in the windows)

can anyone please inform me as to why do i have to put up with&#65279; all this inconsistency? why can't i use my favorite gnome apps in kde and have a decent experience? (i'm not blaming kde, i'm blaming gtk but correct me if i'm wrong) I have more than one computer and on one of my computers i have a gnome desktop installed... i can use ktorrent and vlc and other kde/qt apps in gnome and they look just like gnome (maybe except the icons... if you tell kde to use the icon theme in gnome it will not have replacements for all the kde apps and thus look not too good, but i don't mind that as much, as using oxygen icons is a minor inconsistency, and both the icon sets are awesome)

i also don't get why people that are not within the gnome project are so fond of gtk, i mean firefox and chrome and others...


I hope I wasn't too aggressive in expressing my opinions and that I did not offend anybody. I understand that a lot of free software developers are using their spare time to make a gift to the world, and are not making money out of what they are doing and I appreciate that very much but this is really annoying. What I don't like is that there are many awesome applications in the world of gnu/linux and free software in general, but this fragmentation without a thought for interoperability makes the whole platform not be as good as it could...

---

### Post by SuperSonic4 on 2010-01-25
```
sudo apt-get install gtk-qt-engine
```

You may have to mess about in system settings to find it

---

### Post by roggenschrotbrot on 2010-01-25
in case you are using oxygen with the standard color sheme, [oxygen-molecule]("http://www.kde-look.org/content/show.php/Oxygen-Molecule+KDE+%26+GTK%2B+unified+theme?content=103741") is your best option. i wish there was a better option to combine qt and gtk apps that works with any theme / color sheme though.

---

### Post by ciuci on 2010-01-25
> **roggenschrotbrot said:**
> in case you are using oxygen with the standard color sheme, [oxygen-molecule]("http://www.kde-look.org/content/show.php/Oxygen-Molecule+KDE+%26+GTK%2B+unified+theme?content=103741") is your best option. i wish there was a better option to combine qt and gtk apps that works with any theme / color sheme though.

wow, it is the best clone i have seen so far... but it's still far from pixel perfect. the buttons look quite cumbersome and all in all it still has a "cheap" look to it but the guy did nail the gradient with the titlebar, which is the one thing that bothered me the most and the scrollbars also look really good.

But i think qt actually uses gtk widgets when in gnome, and that's how it manages to look so pixel perfect... is anyone aware of how qt achieves this? if i am right, then that would be the way to go with gtk too ...

---

