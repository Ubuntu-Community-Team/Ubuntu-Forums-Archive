---
title: "[PROJECT] gedit-latex-plugin.deb"
date: 2008-03-17
forum: Desktop Environments
---

### Post by xan.scale on 2008-03-17
i have made a deb package for gedit latex plugin. i have used epm.

In the config file there is this:
```
%product geditlatexplugin
%description A plugin that assists you in handling LaTeX and BibTeX files
%version 0.1.3.1
%copyright GPL 2
%vendor Gnome
%readme README
%license LICENSE
%requires gedit
%requires rubber
%requires python-dbus
```

In the LICENSE fire there is the integral gpl2
In the README file there is this:
```
A plugin that assists you in handling LaTeX and BibTeX files
Copyright © 2007 Michael Zeising
http://live.gnome.org/Gedit/LaTeXPlugin
```

any idea to improve the package?
Someone is interested  the package?
As he put online?

thz bye

---

### Post by xan.scale on 2008-03-18
Nobody cares?

---

### Post by stoffe on 2008-03-24
Hello. I was looking for something that might help with packaging simple plugins, so thanks!

As a comment, I don't think the copyright and vendor fields are correct. According to the man page which I've just skimmed, they should be the copyright string (not license) and vendor or author, respectively.

---

### Post by JoNas-fr on 2008-04-04
Very good idea!!

I am interested into having this deb (Iam building an latex liveCD based on ubuntu with the tool reconstructor and i want to include this plugin).

Could you send it to me by mail?

jonas *DOT* termeau *AT* etu *DOT* univ-nantes *DOT* fr

Thank you!

---

