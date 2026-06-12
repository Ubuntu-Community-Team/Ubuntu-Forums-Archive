---
title: "Installing (new) murrine configurator..."
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by bronze on 2007-07-14
Hi, I've been looking for some eye-candy for Ubuntu and I've found a couple of themes that I like. The thing is that I need the murrine engine to use them, and I have no experience with it. So far I have installed the engine from the repos, but I can't figure out how to use the themes. I have also tried to install "new murrine configurator" from source, but I had no idea how to do it so now it won't work. How do I uninstall it? Is it enough to delete the files in /usr/share/nmc and also /usr/bin?

Think that's about it.
How to use murrine themes,
How to install new murrine configurator.

---

### Post by Theimon on 2007-07-16
Instructions for installing the Murrine configurator are right there in the package. I quote: > For the list of the options availble:
./install.sh --help

INSTALL:
For the normal dance run as root:
./install.sh

If you're using Ubuntu run:
sudo ./install.sh

UNINSTALL:
Just run as root:
./install.sh --uninstall
But you'll need the murrine engine first otherwise it's no use. The Murrine Engine is in the universe repos, so you have to enable those. Then just open Synaptic, do Ctrl+F, enter: murrine engine and it'll pop up the engine.
You can install themes by downloading them from gnome-look.org (for example), then open up the Themes dialogue (System --> Preferences --> Themes) and drag the file you just downloaded onto the dialogue. Or you could select "install theme" and then browse to the right folder

---

