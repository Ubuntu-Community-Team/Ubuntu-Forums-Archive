---
title: "How to get back old ambiance look in 11.04?"
date: 2011-05-28
forum: Desktop Environments
---

### Post by fi2 on 2011-05-28
I have used 11.04 for a while on upgraded machines. It is the first time that I installed it on a clean machine. I goes a lot smoother than the upgraded ones, and I really appreciate the new GUI, but I badly miss the old, Lucid style Ambiance theme. Is there a way to switch back to it?

I downloaded a .deb package, but the package manager does not let me install, stating there is a newer version in use.

Can anybody help please?

---

### Post by drs305 on 2011-05-28
I'm assuming you don't want the 11.04 version of Ambiance? 

If you are looking for the current version: Right click the Desktop and then "Change  Desktop Background"? You can then click on the 'Theme' tab. There should be an Ambiance theme already there. You may also be able to install the older version from the same page via the "Install" button but I would guess that will also produce the 'later version' message. Perhaps if you removed the current Ambiance (again, from the same page) it would allow you to install the older one.

---

### Post by Frogs Hair on 2011-05-28
The wall papers are in the synaptic package manager and the themes can be found at the link . I'm sure the icons are probably available also.
[http://www.webupd8.org/2010/03/new-ubuntu-1004-light-and-dark-themes.html](http://www.webupd8.org/2010/03/new-ubuntu-1004-light-and-dark-themes.html)

---

### Post by Krytarik on 2011-05-28
- right-click on the deb-package
- choose "Open with Other Application..."
- untick "Remember this application..."
- expand "Use a custom command"
- enter "gksudo file-roller"
- click on "Open"
- open the included "data.tar.gz"
- browse to "./usr/share/themes/Ambiance"
- extract its content into something like "/usr/share/themes/Ambiance Lucid"

- open the text editor with "gksudo gedit"
- open the file "/usr/share/themes/Ambiance Lucid/index.theme" from within it
- replace every occurrence of "Ambiance" by "Ambiance Lucid", both reflecting its new path and setting its new name
- save/quit

Now you should be able to choose "Ambiance Lucid" in "Appearance -> Theme".

Greetings.

---

### Post by fi2 on 2011-05-29
Absolutely fantastic. Thank you all.

---

