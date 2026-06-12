---
title: "Cannot get Gedit LateX plugin to work"
date: 2012-04-11
forum: Education &amp; Science
---

### Post by souravc83 on 2012-04-11
I am trying to get Gedit latex plugin to work.
I have tried
1. installing it using Ubuntu Softwar Center. Software Center shows gedit-latex-plugin installed.
2. I have manually put the files (one folder and one file) in the different directories that people have suggested.
These are:
a)~/.gnome2/gedit/plugins
b)/usr/lib/gedit-2/plugins
c) /usr/share/gedit-2/plugins

However, I still do not see the Latex plugin when I go to Gedit Edit->Preferences->Plugins.

I am using using Gedit 3.2.3, Ubuntu 11.10, and Gnome 2.32.1.

I must mention I am not using the Unity Desktop, but the Gnome Desktop, although I don't know if that makes any difference.

Any solutions?

---

### Post by souravc83 on 2012-04-11
With a little bit of google search, it seems that the LaTeX plugin does not work with gedit 3.
Is it then advisable to go back to gedit 2?

[http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

---

### Post by souravc83 on 2012-04-12
Okay, I tried a few things here and there.
I removed Gedit 3.2 which came with my ubuntu, and tried to install Gedit 2.9 from source and then from the Debian package.
That doesn't work because the Gedit 2.x required Gtk 2.0, while Gnome 3 uses Gtk 3.0, so this doesn't quite work.

So, then I went back to Gedit 3.2 and tried to install a version of the latex plugin, that should work for Gnome 3 (although I am not sure it is the official one, since the Gnome website still says that the LaTeX plugin does not work with Gedit 3). I followed the links here.

[http://jaliste.blogspot.com/2011/09/gedit-latex-has-been-ported-to-gedit-3.html](http://jaliste.blogspot.com/2011/09/gedit-latex-has-been-ported-to-gedit-3.html)

I could get a latex plugin allright, but once I enable the plugin, and load a tex document, Gedit crashes. So, no go for me.


So, my question is, is nobody using the LaTex plugin at this moment, after the upgrade to Gnome 3 and Gedit 3? The LaTeX plugin is pretty popular, so I am quite surprised to see that I could not find any known workaround.

Let me know if I am missing something.

---

### Post by AntoineT on 2012-04-13
[https://launchpad.net/~gaspa/+archive/ppa](https://launchpad.net/~gaspa/+archive/ppa) works on my machine (Oneiric 64bit) with gedit 3.2.3

---

### Post by stfields on 2012-04-30
I use this plugin every day, but as of late it has gotten pretty painful.  Installing from 
[https://launchpad.net/~gaspa/+archive/ppa](https://launchpad.net/~gaspa/+archive/ppa)
worked for me as well with gedit 3.2.3.  However, there are plenty of bugs, especially with respect to bibtex integration.

---

### Post by cristianrosa on 2012-05-15
I was also being frustrated with the state of gedit-latex-plugin in 11.10.
I found that you can install a newer version of the plugin (3.4) using the deb package from precise that you can find [here]("http://launchpadlibrarian.net/100908720/gedit-latex-plugin_3.4.0-1_all.deb").
I might improve stability.

---

