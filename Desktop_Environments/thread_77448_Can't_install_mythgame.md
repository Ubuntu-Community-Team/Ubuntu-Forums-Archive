---
title: "Can't install mythgame"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Alibloke on 2005-10-16
Just upgraded to Breezy and tried to install mythfrontend with all the plugins which work fine except for mythgame.

I get:

```
The following packages have unmet dependencies:
  mythgame: Depends: libqt3c102-mt (>= 3:3.3.3) but it is not installable
E: Broken packages
```

If I try to install libqt3c102-mt then I get:

```
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
```

How do I get it to install?

Thanks,

---

### Post by Alibloke on 2005-10-17
*bump*

---

### Post by oblib on 2006-02-09
I just successfully compiled mythgame on my mythTV box. I am writing this from the box, so it will be short (27" CRT does not make a great monitor). 

You need to have whatever package makes it possible to do 'qmake.' I don't know what that package is, if it is not default, I have installed it somewhere in the process of trying to get everything set up. Maybe someone can help me here.

You need to download the source for both mythtv and mythplugins from the mythv webpage. [http://www.mythtv.org/modules.php?name=Downloads&d_op=viewdownload&cid=1](http://www.mythtv.org/modules.php?name=Downloads&d_op=viewdownload&cid=1)
untar them (tar -xvfj myth* or something like that).
For this example, I will have them both out of the same directory (~/sources/ for me). Go to mythplugins-0.xx.x/mythgame/mythgame and type the following:
```

export QTDIR=/usr/share/qt3
export PATH=$PATH;$QTDIR/bin
ln -s ../../../mythtv-x.xx.x/libs/libmyth mythtv  # This should point to your mythtv source libs directory
cd ..
sudo qmake mythgame.pro
sudo make
sudo make install

```
The install script installed the plugin to /usr/local/lib/mythtv/plugin, but on my machine, it should have gone in /usr/lib/mythtv/plugin so do this
```

sudo cp mythgame/libmythgame.so /usr/lib/mythtv/plugins/
sudo cp /usr/local/share/mythtv/* /usr/share/mythtv/ -R

```
You could probably fix the makefile, but I didn't want to bother with that. At that point, it should show up as an option under Media Library->Play Games. My install came up with a warning about supporting xmame, but I don't play mame games, so I haven't bothered looking into that yet.

---

