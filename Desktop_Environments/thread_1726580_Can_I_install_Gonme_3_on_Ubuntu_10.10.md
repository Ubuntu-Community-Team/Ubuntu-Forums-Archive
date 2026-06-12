---
title: "Can I install Gonme 3 on Ubuntu 10.10"
date: 2011-04-11
forum: Desktop Environments
---

### Post by swapnilchitnis360 on 2011-04-11
I'm downloading Ubuntu 11.04 Beta 1 now but I can't wait to try Gnome 3 on Ubuntu 10.10. Is there any way I can do that?

---

### Post by 3Miro on 2011-04-11
Both 10.10 and 11.04 come with Gnome 2.32. To use Gnome 3, you will have to use the unofficial PPA:

[http://blogs.gnome.org/rodrigo/2011/04/11/unofficial-gnome3-on-ubuntu-ppa/](http://blogs.gnome.org/rodrigo/2011/04/11/unofficial-gnome3-on-ubuntu-ppa/)

Note that this may be causing some problems.

---

### Post by BbUiDgZ on 2011-04-11
or you could just install debian squeeze complete with gnome 3

---

### Post by Copper Bezel on 2011-04-11
Related question: If I install the latest version of Compiz and Emerald on 10.10 or 11.04, would I be able to use Gnome 3 (not Shell) with Compiz as the WM and Emerald as the decorator, or are there conflicts between any of them?

---

### Post by cbowman57 on 2011-04-11
Open the terminal and run the following commands

sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
sudo apt-get update
sudo apt-get install gnome3-session

After completing the installation Log out and back in, selecting the GNOME Session in GDM

[http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html]("http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html")

---

