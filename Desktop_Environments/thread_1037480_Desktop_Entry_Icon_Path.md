---
title: "Desktop Entry Icon Path"
date: 2009-01-11
forum: Desktop Environments
---

### Post by martino2k8 on 2009-01-11
I'm using KDE4 and I've been trying to set an icon for a folder with a picture that is located in that specific folder with a relative path (ie *Icon=cover.jpg*), however this doesn't work. It only works when I use the full path (ie *Icon=/home/user/Music/Mai-HiME/Mai-HiME Original Soundtrack Vol. 2 - Mai/cover.jpg*). 

Is it not supposed to work with relative paths or am I missing something?


Thanks

---

### Post by Endolith on 2009-05-05
I have the same problem in Gnome.  ./filename.png and ~/filename.png don't work, either.

[http://www.mail-archive.com/xdg@lists.freedesktop.org/msg04553.html](http://www.mail-archive.com/xdg@lists.freedesktop.org/msg04553.html)

[https://answers.launchpad.net/ubuntu/+question/67526](https://answers.launchpad.net/ubuntu/+question/67526)

So Gnome uses desktop entry files as "Launchers", but they don't function very much like the Launchers in other OSes...

---

