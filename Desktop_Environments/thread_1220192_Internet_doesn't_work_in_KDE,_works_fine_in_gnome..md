---
title: "Internet doesn't work in KDE, works fine in gnome."
date: 2009-07-22
forum: Desktop Environments
---

### Post by karimruan on 2009-07-22
Hi guys, I am running Ubuntu Jaunty with some extra DE's installed, namely KDE, E16 and LXDE. I really want to use KDE, but, the internet doesn't seem to work with it. It works fine with gnome. Actually, it only works with gnome. I love the way KDE looks and was wondering if anyone could help me with this problem. Here are my specs:

HP DV6700 laptop 
Atheros Wi-fi card Not sure of driver version
using cable internet on a dual boot with Windows Vista. 
I only tried too include what may have been necessary.

Thank you for your time.

---

### Post by 67GTA on 2009-07-22
Is it a WPA connection? If so, there is a bug with the KDE4 network manager that keeps it from connecting to encrypted connections. It should be fixed before long. Until then I would try wicd. I use it instead of the Gnome or KDE managers.

---

### Post by Zorael on 2009-07-22
The KDE network manager applet has a bit of a bad track record. Hopefully it'll be better in 4.3, which should (?) hit Jaunty backports when released later this month.

Alternatively/in the meantime, you may want to grab and install **wicd**, but unless you have a working Internet connection that might be a bit difficult. Borrow a friend's wired connection. :3

It's in the universe repositories, and also available for download over at [packages.ubuntu.com](http://packages.ubuntu.com/jaunty/wicd).

If you really really can't get net access on your machine, just do the following in a terminal and see what packages it feels it must download (at a minimum) to get wicd installed. Jot the names down, download those .debs from packages.ubuntu.com on /another/ system, copy them over to the machine in quesiton (usb stick), and install them manually.
```
$ aptitude install wicd -sv --without-recommends
```
It should spout something like this.
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  plasma-widget-network-manager
The following NEW packages will be installed:
**  python-cairo{a} python-glade2{a} python-gtk2{a} python-urwid{a} wicd**
The following packages will be REMOVED:
  network-manager{a}
The following packages are SUGGESTED but will NOT be installed:
  python-gtk2-doc python-numpy
0 packages upgraded, 5 newly installed, 1 to remove and 0 not upgraded.
Need to get 2435kB of archives. After unpacking 8229kB will be used.
The following packages have unmet dependencies:
  plasma-widget-network-manager: Depends: network-manager but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
plasma-widget-network-manager

Score is 119

Accept this solution? [Y/n/q/?]
The following NEW packages will be installed:
  **python-cairo{a} python-glade2{a} python-gtk2{a} python-urwid{a} wicd**
The following packages will be REMOVED:
  network-manager{a} plasma-widget-network-manager{a}
The following packages are SUGGESTED but will NOT be installed:
  python-gtk2-doc python-numpy
0 packages upgraded, 5 newly installed, 2 to remove and 0 not upgraded.
Need to get 2435kB of archives. After unpacking 6500kB will be used.
Do you want to continue? [Y/n/?]
Remv plasma-widget-network-manager [0.0+svn976478-0ubuntu1]
Remv network-manager [0.7.1-0ubuntu1]
[B]Inst python-cairo (1.8.4-3exp2ubuntu1 Ubuntu:9.10/karmic)
Inst python-gtk2 (2.15.2-0ubuntu1 Ubuntu:9.10/karmic)
Inst python-glade2 (2.15.2-0ubuntu1 Ubuntu:9.10/karmic)
Inst python-urwid (0.9.8.4-1 Ubuntu:9.10/karmic)
Inst wicd (1.6.1-3 Ubuntu:9.10/karmic)[/B]
Conf python-cairo (1.8.4-3exp2ubuntu1 Ubuntu:9.10/karmic)
Conf python-gtk2 (2.15.2-0ubuntu1 Ubuntu:9.10/karmic)
Conf python-glade2 (2.15.2-0ubuntu1 Ubuntu:9.10/karmic)
Conf python-urwid (0.9.8.4-1 Ubuntu:9.10/karmic)
Conf wicd (1.6.1-3 Ubuntu:9.10/karmi
```
...with the packages in bold being dependencies you'd have to download alongside wicd to get it to install.

---

### Post by karimruan on 2009-07-22
Okay, I downloaded wicd, and now I cannot access the internet at all, even in gnome. In gnome, it says that the connection requires that I enable encryption. I don't know how to do that, and I just want it to work in kde. Any help for getting kde to work now?

---

### Post by Zorael on 2009-07-22
Look through your menus for the wicd tray icon application, or the configuration app.

---

### Post by karimruan on 2009-07-22
Thanks everyone, I got it working. All I had to do was click on the connection and a menu appeared, I entered in my passphrase and that was it. Oh, I had to use the wext driver not ndiswrapper.

Thanks again!

---

### Post by 67GTA on 2009-07-22
Once you find and open wicd, look for the connection you want and click on the "advanced" button. Then enter your key and click connect. You can also check the "Automatically connect" box if it is a connection you want to auto connect to at boot. After doing this, the wicd applet should auto start in the panel each time you boot.

---

### Post by necron53 on 2009-08-01
Thank You Zorael. I had the same exact issue as karimruan had. Reading through the posts in he forums I came across your post. I followed your advice and got wicd installed and I'm up and running. 
Thank you again for helping this newbie.

---

### Post by Dullstar on 2009-08-01
Basis:

First, go into KDE.
Second, find the network connection thing.
Third, put in the appropriate things.
Fourth:  There is no fourth.

---

