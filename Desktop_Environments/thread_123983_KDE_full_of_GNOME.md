---
title: "KDE full of GNOME"
date: 2006-01-31
forum: Desktop Environments
---

### Post by ashrack on 2006-01-31
installed  but removed it 10min after. thank god I have DEBFOSTER installed.

When I installed KUBUNTU-DESKTOP yesterday and started it, I got all of the GNOME icons in the KDE start menu aswell. It was I mess, couldn't get arround anything and am pretty much used to KDE, since I've been using it for half a year in Mandriva. So I went back to GNOME to find out that in GNOME menu there's also a lot of KDE icons and entries OMG.
its needless to say that I purged KDE soon after with debfoster, so nothing remained of it.

To my question, just had to tell U all my story;)
Is it possible to instal KUBUNTU-DESKTOP and then not have GNOME specific icons in the K menu? Or must I install KUBUNTU on another partition?

---

### Post by Sutekh on 2006-01-31
[QUOTE=ashrack]installed  but removed it 10min after. thank god I have DEBFOSTER installed.

When I installed KUBUNTU-DESKTOP yesterday and started it, I got all of the GNOME icons in the KDE start menu aswell. It was I mess, couldn't get arround anything and am pretty much used to KDE, since I've been using it for half a year in Mandriva. So I went back to GNOME to find out that in GNOME menu there's also a lot of KDE icons and entries OMG.
its needless to say that I purged KDE soon after with debfoster, so nothing remained of it.

To my question, just had to tell U all my story;)
Is it possible to instal KUBUNTU-DESKTOP and then not have GNOME specific icons in the K menu? Or must I install KUBUNTU on another partition?[/QUOTE]
YES.

Two ways of doing it.  First way is to use the Menu Editor in GNOME (Applications -> System Tools -> Menu Editor) and uncheck each of the KDE programs you don't want in GNOME.  I'm not sure if there is an equivalent program in KDE though, which leads to method two.

Each program has a .desktop file located in /usr/share/applications and /usr/share/applications/kde

The applications will show up in GNOME and KDE unless you add a line in each and every .desktop file, such as
```
OnlyShowIn=KDE;
```
Fortunately [Xian]("http://www.ubuntuforums.org/member.php?u=37") has got a script to do that for you
[http://www.ubuntuforums.org/showpost.php?p=532770&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=532770&postcount=2")

To go the other way and remove GNOME entries in KDE, slightly modify the code
```
cd /usr/share/applications/
sudo chmod a+rw /usr/share/applications/*
for i in *; do echo "OnlyShowIn=GNOME;" >> $i; done
sudo chmod 644 /usr/share/applications/*
```

---

### Post by Adrian on 2006-01-31
I wrote a small HOWTO about this earlier today. You may want to check out the second solution:
[http://www.ubuntuforums.org/showthread.php?t=123969](http://www.ubuntuforums.org/showthread.php?t=123969)

---

