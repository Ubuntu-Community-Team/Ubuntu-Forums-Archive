---
title: "SLED Slab install problems"
date: 2006-09-19
forum: Desktop Environments
---

### Post by adie273 on 2006-09-19
Wonder if anyone could help me out,

Had the Ubuntu port of SLED Slab installed on my ubuntu setup last week. An update of compiz screwed things up so badly my system wouldn't go further than GDM.

Anyway, reinstalled everything, and went to install SLED Slab now and i'm getting this...

[I]gnome-main-menu:
  Depends: libpanel-applet2-0 (>=2.14.2) but 2.14.1-0ubuntu16 is to be installed
  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed[/I]

Anyone know how i can get this installed, I could go through the hassle of trying to solve the problem myself, but been working loads lately, so i'm shattered and quite frankly can't be bothered if someone else can happen to help me out :) 

Thanks in advance for any help, much appreciated

Adie

---

### Post by orb9220 on 2006-09-19
Don't know if you know that we have a forum called usp ubuntu system panel that works just like sled

[http://www.ubuntuforums.org/forumdisplay.php?f=156](http://www.ubuntuforums.org/forumdisplay.php?f=156)

---

### Post by adie273 on 2006-09-19
yea seen it, got it installed, but personally i don't like it, VERY large and don't like how the applications part expands slightly when i goto "All Applications" (Just a little thing that bugs me).

If these things can be sorted right enough i'd use it.

Thanks anyway

---

### Post by konst88 on 2006-09-19
use aptitude instead of pat-get. it will solve any dependencies problems.
the usage is the same as with apt-get, just instead of apt-get, write aptitude.

---

### Post by adie273 on 2006-09-19
Tried Aptitude and got the following...

> The following packages are BROKEN:
  gnome-main-menu
The following NEW packages will be automatically installed:
  libglitz1
The following packages have been kept back:
  libwnck18
The following NEW packages will be installed:
  libglitz1
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 412kB of archives. After unpacking 1508kB will be used.
The following packages have unmet dependencies:
  gnome-main-menu: Depends: libpanel-applet2-0 (>= 2.14.2) but 2.14.1-0ubuntu16 is installed.
                   Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnome-main-menu [Not Installed]

Score is -1


Anyone any idea as to why this won't install now, but installed last time i tried with ease?

(I know its a dependancy issue, but i've no idea where i got the libraries it needs before, i didn't do anything last time that i didn't do on this install. Unless this is an updated SLED slab deb from the last one i used)

---

