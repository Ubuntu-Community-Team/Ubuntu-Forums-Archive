---
title: "Qt apps in Kubuntu 16.04 get wrong app style"
date: 2017-03-30
forum: Desktop Environments
---

### Post by thomi_ch on 2017-03-30
Hey Community

Since i upgraded to Kubuntu 16.04 i got a issue, that on Kdialog's (File Open) in different Apps like Chrome, Libreoffice the layout of file dialog is not like system standard (Breeze). Maybe also on other places, but i only reconized this one.
. Scrollbars and Buttons not correct
. Default single click not working

I searched around and checked each config file (~/.config/, ~/.kde/share/config) and tried to figure out, which does make the problem.

At last i found it ;)
~/.config/Trolltech.conf
Trolltech.conf does hold the Qt config settings, read more at [https://wiki.archlinux.org/index.php/qt]("https://wiki.archlinux.org/index.php/qt")

I just renamed original one to eg. Trolltech.conf_tmp and re logged into my system. All done !
I just needed to set some few settings to fit my old style, thats it...

Some Screenshots, compare Scrollbars, Icons and Buttons...

before
[ATTACH=CONFIG]274356[/ATTACH]
[ATTACH=CONFIG]274355[/ATTACH]

after
[ATTACH=CONFIG]274357[/ATTACH]
[ATTACH=CONFIG]274358[/ATTACH]

Hope that can help others ;)

regards
thomi

---

