---
title: "Unable to run &quot;Avant WIndow Navigator&quot;"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by sarahsilverman on 2008-01-05
I have been following the instructions here : [http://www.ubuntugeek.com/howto-install-avant-window-navgator-in-ubuntu-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-avant-window-navgator-in-ubuntu-gutsy-gibbon.html)

I am stuck in the "Preparing Your System" part. I'm at the "make" part, it keeps saying that there isn't anything to do with "./autogen.sh".

How do I fix this? I really want this, even though I don't need it. But isn't that the point of having Ubuntu for its really cool Desktop Effects.

It keeps saying:
"jonathan@jonathan-laptop:~/awn-extras/awn-applets/awn-extras-applets$ make
make: *** No targets specified and no makefile found.  Stop."

I followed the guide exactly.

Thanks for helping :)

---

### Post by steeleyuk on 2008-01-05
Here's what i'd do. Go to Launchpad and download the [0.2.1 version]("https://launchpad.net/awn/+download"). Install all the dependencies that AVN needs (if you haven't already):

> sudo apt-get install build-essential automake1.9 autotools-dev bzr libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf gnome-common python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev

Unpack the tar file and run the following commands:

./configure
make
sudo make install (you'll be asked for your password at this point).

To be honest, I don't know why the article suggests you download using BZR, maybe will just grab the latest files. However the 0.2.1 version is the latest official build.

---

### Post by sarahsilverman on 2008-01-07
> **steeleyuk said:**
> Here's what i'd do. Go to Launchpad and download the [0.2.1 version]("https://launchpad.net/awn/+download"). Install all the dependencies that AVN needs (if you haven't already):



Unpack the tar file and run the following commands:

./configure
make
sudo make install (you'll be asked for your password at this point).

To be honest, I don't know why the article suggests you download using BZR, maybe will just grab the latest files. However the 0.2.1 version is the latest official build.

thank you so much, this worked for me.

---

