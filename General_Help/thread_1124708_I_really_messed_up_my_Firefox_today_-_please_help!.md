---
title: "I really messed up my Firefox today - please help!"
date: 2009-04-13
forum: General Help
---

### Post by xg7 on 2009-04-13
Today I started FF in "safe mode" and reset all user settings to default.  I did this in order to reset all the about:config setting I tweaked that seemed to be lagging my connection.

When I restarted FF, all history & bookmarks were gone and it wasn't logging any new activity; that is, if I would go to a new page, the back button wouldn't activate so I could go back a page & nothing was being logged in history!

I decided to reinstall the FF meta package, but got the same result.  Then I tried starting FF in safe mode again and ALL my old history & bookmarks are back!  The only thing that's been reset are the about:config settings and my toolbar preferences.  So how do I get it to stay like this (meaning I want it to start like this automatically)?

Thanks VERY much! :)

---

### Post by lovinglinux on 2009-04-13
Looks like a corrupted FF profile. 

Create a new profile and import the bookmarks from the old one.

You can use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to backup extensions, preferences, passwords, permissions, cookies and other stuff from your old profile and restore them into the new one. All backup and restore operations should be done through your old profile. When restoring, it will ask for the profile to restore to, but you can't restore to an active profile.

I also recommend not backing up and  restoring the entire profile at once, because you might restore the problem to new profile.

---

### Post by saidinesh5 on 2009-04-13
1) Back up only your important data like bookmarks ,extensions etc.. n stuff using FEBE(thats a firefox addon).
2) delete the .mozilla folder from your your home profile
3) start firefox and install FEBE (you can even install FEBE from your back up)
4)restore your old data using FEBE
:)

---

