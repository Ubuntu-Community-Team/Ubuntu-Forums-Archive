---
title: "Language problem in apps (all in squares)"
date: 2016-02-11
forum: Desktop Environments
---

### Post by Share_The_Pain on 2016-02-11
Hello people, i already tryed to check all the settings about language definitions but still the apps like vlc and spotify appear all in squares. 

Im using xubuntu 14.04.3 LTS and my default language is portuguese. 

Kind regards

---

### Post by slickymaster on 2016-02-11
What exactly do you mean by "... appear all in squares"? Can you provide us a screenshot?

---

### Post by Share_The_Pain on 2016-02-11
[IMG]http://s11.postimg.org/5kyin7p4j/Screenshot_12_02_2016_00_34_17.jpg[/IMG]

---

### Post by slickymaster on 2016-02-11
Are you facing that problem only with those two applications? I'm asking it because both use QT GUIs, not GTK+

---

### Post by Share_The_Pain on 2016-02-12
HUmm... sorry for the late reply, i just installed xubuntu and yes probably is that. Im gonna have a look if that package is installed. Thank you slickymaster!

---

### Post by Share_The_Pain on 2016-02-12
[IMG]http://s8.postimg.org/lzwipd5mt/Screenshot_13_02_2016_00_18_44.png[/IMG]

I'm going to change language settings to Inglês to see if it changes the problem with the squares... :/

---

### Post by buzzingrobot on 2016-02-13
I  *think *those squares show up when there's a problem with fonts. That is, the app can't find them, or use them for some reasons.  Text in the panel and the window decorations is rendered correctly in your screenshots.

XFCE has one font setting, in the Appearances tool, I think.  It's probably set to Sans by default, which on Ubuntu releases maps to Dejavu.  (The package is "fonts-dejavu"). 

There is a tool -- qt4-qtconfig -- that allows setting a font family for QT apps, among other things.  It's in the repos.

---

### Post by slickymaster on 2016-02-15
> **buzzingrobot said:**
> I  *think *those squares show up when there's a problem with fonts. That is, the app can't find them, or use them for some reasons.  Text in the panel and the window decorations is rendered correctly in your screenshots.

XFCE has one font setting, in the Appearances tool, I think.  It's probably set to Sans by default, which on Ubuntu releases maps to Dejavu.  (The package is "fonts-dejavu"). 

There is a tool -- qt4-qtconfig -- that allows setting a font family for QT apps, among other things.  It's in the repos.

+1

Default font in Xubuntu is Droid Sans.

---

