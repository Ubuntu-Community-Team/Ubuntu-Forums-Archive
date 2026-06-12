---
title: "Konqueror starts up instead of Nautilus, no desktop (URGENT)"
date: 2009-05-06
forum: Desktop Environments
---

### Post by Freckletoe on 2009-05-06
I'm using Ubuntu 9.04
So I've had some trouble with my desktop as of late and the short of it is that I uninstalled all of the file managers on my system (Nautilus, Konqueror, Dolphin) and only reinstalled nautilus. (I have no desktop at this point) So I go into gconf-editor to change my preferences and find that the 'show_desktop' box is checked, but still no desktop. 

So I try to open a folder and it won't open, which shouldn't happen. So I went into the terminal and typed in 'nautilus' and it came up and said that Nautilus wasn't installed. So I tried apt-get and it said that it didn't install, delete, upgrade any files so that said to me that Nautilus was, indeed, installed. 

Next, in order to do some file managing, I installed Konqueror. It's ok, and I liked it for about 2 days and used this website to make it my default [http://www.psychocats.net/ubuntu/nonautilusplease]("http://www.psychocats.net/ubuntu/nonautilusplease"); then I got fed up with it, so I used the restorenautilus script at the bottom of that website and it didn't work. So I tried opening nautilus through the terminal, typed in 'nautilus' and it started konqueror!

To fix this problem, some gus on the IRC told me:
reinstall ubuntu-desktop (GNOME) (didn't work)
He gave me his Nautilus file settings (didn't work)


When I type nautilus into the terminal it comes up with this: konqueror(9836) KonqViewManager::setCurrentProfile: "webbrowsing" localPath= "/home/bryce/.kde/share/apps/konqueror/profiles/webbrowsing"    Then starts Konqeuror


So as of now I have:
-no desktop
-a limited knowledge of the terminal
-a headache

What should I do to get Nautilus up and running again, and by extension, my dekstop?

---

