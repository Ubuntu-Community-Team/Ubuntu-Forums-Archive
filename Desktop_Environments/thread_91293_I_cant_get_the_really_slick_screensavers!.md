---
title: "I cant get the really slick screensavers!"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Canuckelhead on 2005-11-16
Anyone have any tips on how to get the Really slick screensavers to work?

---

### Post by Kapre on 2005-11-16
[QUOTE=Canuckelhead]Anyone have any tips on how to get the Really slick screensavers to work?[/QUOTE]

Canuckel - which screensavers are you talking about here? 

K

---

### Post by Canuckelhead on 2005-11-16
specifically matrix view, hyperspace, euphoria... they are from the RSS-glx  package..

---

### Post by Ric Fischer on 2005-12-12
[FONT="Tahoma"][QUOTE=Canuckelhead]Anyone have any tips on how to get the Really slick screensavers to work?[/QUOTE]
Open a regular terminal window (root not needed and not recommended for last command) and type in the following three comands:

```
killall xscreensaver
rss-glx_install.pl
xscreensaver -nosplash &
```
Apparently, the rss-glx package in the repository doesn't run the rss-glx_install.pl program after downloading and "installing" the files.

Skyrocket is my favorite.

-- 
Ric Fischer[/FONT]

---

### Post by testube_babies on 2006-04-23
Can anyone get this to work on Dapper?  I hate GNOME-Screensaver, so I got rid of it in favor of XScreensaver, but now I don't have the really slick pack.

---

