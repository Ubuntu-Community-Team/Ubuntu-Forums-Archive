---
title: "wine makes gdm restart"
date: 2006-05-05
forum: Gaming &amp; Leisure
---

### Post by siman on 2006-05-05
I installed wine from the default ubuntu repos that already were in the source.list - I was only playing SoF2 and Max payne 2. Everything worked out of the box: apt-get wine, wine Setup.exe, wine Sof2.exe => playing the game

I wanted to try Serious Sam 2, so I installed the newest wine (9.12?) with apt-get after including wine.sourceforge.net in repos.

The new wine didn't help with SS2 and Sof2 & MP2 crashed all the time, so I uninstalled the new wine and reinstalled the one from the universe (?) repos.

Now when I start one of my games with the old wine (that already worked perfectly), the screen goes black and I get thrown back to the login-screen!!!

In xorg.0.log.old it says

```

Fatal server error:
Caught signal 11.  Server aborting

```

update: ähm, me silly.. I never installed the old wine. whatever I do it keeps on installing the new one. i tried apt-get clean and will investigate further.. damn

update2: I don't know how I did it, but apt-get remove never really removed the new wine - i had to manually remove /usr/lib/wine, etc. folders and than to a fresh install.... I know this is bad, but it works for now

[[DEL ME: I think I didnt cleanly remove one of the wines before installing another one - this might be a problem. Any ideas what I can do or which logs to check for further info?]]

---

