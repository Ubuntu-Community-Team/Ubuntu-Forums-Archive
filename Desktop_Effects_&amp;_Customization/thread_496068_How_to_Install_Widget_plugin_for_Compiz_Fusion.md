---
title: "How to: Install Widget plugin for Compiz Fusion"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by jessegillies on 2007-07-08
Thanks to the author of [this post]("http://forum.ubuntuusers.de/viewtopic.php?p=813159#813159"), I was able to get the Widget plugin installed for Compiz Fusion. You don't need to make the changes to the file widget.c that the author talked about. Just make it and install it!

1. sudo apt-get install gcc libtool cogito libxslt1-dev libxml2-dev compiz-dev
2. git clone git://people.freedesktop.org/~mike/widget
3. cd widget
4. make
5. sudo make install
6. sudo killall compiz.real
7. compiz --replace

Now you should have the Widget plugin in ComipzConfig Settings Manager! Woohoo!

---

