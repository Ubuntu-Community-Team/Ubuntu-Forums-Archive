---
title: "How to: Install Doomsday Engine (inc. snowberry) for ubuntu 8.04, 8.10 and 9.04"
date: 2009-09-22
forum: Gaming &amp; Leisure
---

### Post by Bluefist on 2009-09-22
Installing Doomsday Engine for doom games (including snowberry launcher) on Ubuntu 8.04, 8.10 or 9.04.

Just a little how to for prosperity. Now, installing the doomsday engine is not difficult as it is available as a deb (compiled by Yagisan) from the dengine hq site [here]("http://www.dengine.net/dew/index.php?title=Installation_%28Unix%29#Pre-built_Debian_.2F_Ubuntu_packages"). The trick is in setting up the snowberry frontend as it is not included with the debs for ubuntu.

For the purpose of this guide I installed deng_1.9.0-beta6.6-1_i386.deb on hardy.

First make sure you have snowberry's dependencies: python and a recent wxpython (available here at [wxpython.org]("http://wiki.wxpython.org/InstallingOnUbuntuOrDebian"))

To get a the latest wxpython add this key to your your apt's list of trusted keys
```
curl [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) | sudo apt-key add - 
```

Add following to your sources list
```
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) hardy-wx main
deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) hardy-wx main
```

Update your sources, then install python-wxgtk2.8 from synaptic
```
sudo apt-get install python-wxgtk2.8
```

Then install snowberry
```
sudo apt-get install subversion
svn co [https://svn.sourceforge.net/svnroot/deng/trunk/snowberry](https://svn.sourceforge.net/svnroot/deng/trunk/snowberry) snowberry
```

Now open and edit "snowberry.py"
```
gksudo gedit /home/bluefist/snowberry/snowberry.py
```

Add "#!/usr/bin/python" without quotation marks as the first line in the script, and make it executable.

Now run snowberry.py from the terminal
```
cd /home/bluefist/snowberry/
python snowberry.py
```

Doomsday Engine Frontend should launch and start a setup wizard, tell it where the wads for doom, doom 2, hexen etc. are (I suggest a folder in your home folder called doomsday) and setup addons/display/sound settings to suite yourself.

Creating a launcher for the client, to do this I created a simple script in my home folder by opening a empty file (lets call it "snowberry launcher") and pasting in the following (replacing your name with mine) and Make the script executable.

```
#!/bin/bash
cd /home/bluefist/snowberry/
python snowberry.py
exit
```Then you can just create a launcher on your desktop/ applications menu by pointing it at this script.

---

### Post by afrodeity on 2010-08-09
Thanks for the great tutorial. I've updated it here:

[http://indlovu.wordpress.com/2010/08/08/playing-doom-legacy-on-ubuntu-lucid/](http://indlovu.wordpress.com/2010/08/08/playing-doom-legacy-on-ubuntu-lucid/)

---

