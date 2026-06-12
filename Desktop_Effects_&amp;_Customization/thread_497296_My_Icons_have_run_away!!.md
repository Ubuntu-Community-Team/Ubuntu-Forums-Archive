---
title: "My Icons have run away!!"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by derby007 on 2007-07-10
Since every other thread is about Beryl or Compiz, I'll start a diff one. After I picked a diff Icon theme, the Icons for the 'ShutDown menu' are missing, ie. when u click on the shutdown option at the top right hand corner of Ubuntu. Any ideas on how to get new icons displayed in this menu?

---

### Post by bluknight on 2007-07-11
Happened exactly to me:
[http://ubuntuforums.org/showthread.php?t=498132](http://ubuntuforums.org/showthread.php?t=498132)
Someone has submitted a bug report on missing icons but don't seem to read ANY response from Devs and other coffee gulpers on this. Wonder why :confused::confused::confused:
[http://ubuntuforums.org/showthread.php?t=482939](http://ubuntuforums.org/showthread.php?t=482939)

EDIT:  Try
System->Preferences->Theme->Customize->Icons Select KDE-Classic
OR in a shell type:kcontrol
Go to Appearance & Themes -icons and select KDE-Classic
cp -r crystalsvg /usr/share/icons/ (default.kde mangled by installing kde and removing)
Now all restored - including amarok !!

---

