---
title: "Steam wont open after fresh OS installation."
date: 2015-05-28
forum: Gaming &amp; Leisure
---

### Post by deniz4 on 2015-05-28
Hi! When I tried to launch steam i get this error in Debian "jessie" 8.

```
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2015-05-28 15:38:01] Startup - updater built Aug 26 2014 15:35:42
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)
```


Since ubuntu forums used more frequently and this is a gaming sub-forum, i figured i can ask here since in main debian forums no one was able to help.
By the way, followed this site to install Steam. [U][URL="https://wiki.debian.org/Steam"]https://wiki.debian.org/Steam

[/URL][/U]This is my bootstrap_log.txt in ~/Steam/logs if this can help

```
[2015-05-28 15:25:06] Startup - updater built Aug 26 2014 15:35:42 
 
 
[2015-05-28 15:32:25] Startup - updater built Aug 26 2014 15:35:42 
 
 
[2015-05-28 15:32:38] Startup - updater built Aug 26 2014 15:35:42 
 
 
[2015-05-28 15:34:50] Startup - updater built Aug 26 2014 15:35:42 
 
 
[2015-05-28 15:38:01] Startup - updater built Aug 26 2014 15:35:42
```

Thanks in advance!


PS: I did this once before and it caused my Gnome to fail with infamous "Oh no... Something went wrong" screen, so i'm thinking that i'm doing something wrong here. But i couldn't figure out what.

---

### Post by efflandt on 2015-05-29
Have you checked out the **Steam for Linux** forum [http://steamcommunity.com/app/221410/discussions/0/558750544046857041/](http://steamcommunity.com/app/221410/discussions/0/558750544046857041/)

Also you may get more useful error messages launching steam from a terminal window. What graphics and graphics drivers are you using (nvidia seems to work best at this time)?

---

### Post by Richard_Romick on 2015-05-30
Please post the results of

inxi -Fxz

Make sure your terminal window is wide enough to show all results without word wrap.

---

