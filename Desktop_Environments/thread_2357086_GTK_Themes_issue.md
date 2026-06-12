---
title: "GTK Themes issue"
date: 2017-03-29
forum: Desktop Environments
---

### Post by elitancre on 2017-03-29
Hi everyone, i'm new to this forum. I downloaded some themes and most of them don't "work" well. In some cases there is no spacing between tab titles inside a window, and no border between ON/OFF switches. I will attach some screenshots
Thanks in advance.
Elia Tancredi.
[ATTACH=CONFIG]274352[/ATTACH][ATTACH=CONFIG]274353[/ATTACH]

---

### Post by Dennis N on 2017-03-29
The theme you use must be made for the version of libgtk-3 used by your version of Ubuntu. If not, you get little glitches like the crowded menu titles.

Find libgtk-3 version:
Example: This OS needs themes made for gtk 3.14:
```
dmn@Sydney:~$ dpkg-query --list libgtk-3*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-========================================================================
ii  libgtk-3-0:amd64                  [COLOR="#FF0000"]3.14[/COLOR].13-0ubuntu1      amd64                 GTK+ graphical user interface library
ii  libgtk-3-bin                      3.14.13-0ubuntu1      amd64                 programs for the GTK+ graphical user interface library
ii  libgtk-3-common                   3.14.13-0ubuntu1      all                   common files for the GTK+ graphical user interface library
```
When finding themes from external sources, it's important to check the gtk support on the theme's web page.

---

### Post by elitancre on 2017-03-30
so not every theme is compatible with my gtk version right? i have gtk 3.20, one of this themes causing glitches is Arc, it's quite famous, but i couldn't find a version with 3.20 compatibility online...

---

### Post by coffeecat on 2017-03-30
*Thread moved to **Desktop Environments**,* for technical support.

(Art & Design is not a support area.)

---

### Post by Frogs Hair on 2017-03-30
> **elitancre said:**
> so not every theme is compatible with my gtk version right? i have gtk 3.20, one of this themes causing glitches is Arc, it's quite famous, but i couldn't find a version with 3.20 compatibility online...

What release of Ubuntu are you using ?

---

