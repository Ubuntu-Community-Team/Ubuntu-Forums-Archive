---
title: "desktop switcher not working properly"
date: 2010-03-07
forum: Desktop Environments
---

### Post by sandu.lulu on 2010-03-07
cannot switch between multiple workspaces using the mouse scroll or using keyboard. windows+e also shows only one workspace. each workspace seems to be treated separately. each workspace sees only the applications that were launched in it although in the task bar appear all the applications (awn is configured to show the apps in all workspaces). 

i attached some screen shots of each workspace with some comments on them.

this happened after i selected none in the visual effects tab. changed it back and now it's like this.
i reinstalled compiz with no luck.
i use ubuntu 9.04

---

### Post by erginemr on 2010-03-07
It may seem an idiotic reply but did you try restarting the computer? I believe Compiz did not "understand" that you have turned it back on.

---

### Post by sandu.lulu on 2010-03-08
> **erginemr said:**
> It may seem an idiotic reply but did you try restarting the computer? I believe Compiz did not "understand" that you have turned it back on.


i have restarted. it's been 2 days since this occurred and no change or fix could be found.

still need help!

---

### Post by erginemr on 2010-03-08
Hmm, let's try resetting Gnome's settings.

When issued from the terminal in your home directory, these commands will take a backup of the current Gnome settings and reset them:
```
mv .gnome2 .gnome2.bak
mv .gconf .gconf.bak
mv .gconfd .gconfd.bak

```

---

### Post by hariks0 on 2010-03-08
Wait... Please check the compiz settings is something like the attachments. Post screenshots of your ccsm otherwise. Karmic allows multiple desktop count to only 1 and horizontal or/and vertical sizes to > 1. But Jaunty can set 4 [as in your case or more]. Tht may be the reason.

---

### Post by sandu.lulu on 2010-03-08
> **hariks0 said:**
> Wait... Please check the compiz settings is something like the attachments. Post screenshots of your ccsm otherwise. Karmic allows multiple desktop count to only 1 and horizontal or/and vertical sizes to > 1. But Jaunty can set 4 [as in your case or more]. Tht may be the reason.

that was indeed the reason. problem solved, now i'm just confused and still don't know why the settings changed in the first place. 

thank you very much erginemr and hariks0 for your helpful replies.

---

