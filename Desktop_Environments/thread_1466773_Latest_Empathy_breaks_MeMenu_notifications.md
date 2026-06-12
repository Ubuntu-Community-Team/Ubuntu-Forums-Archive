---
title: "Latest Empathy breaks MeMenu notifications"
date: 2010-04-30
forum: Desktop Environments
---

### Post by splatterdash on 2010-04-30
I'm on 10.04.

I was curious to see the new features implemented (mainly geo-location) in Empathy, so I added their PPA and did an update. After updating, the notifications for Empathy become separated from the MeMenu (separate icons, no 'Chat' option is specified when I click the MeMenu), although I can still update my status by clicking on my user name.

Does anyone know how to integrate the new Empathy back into MeMenu? If not, how can I roll back to the previous Empathy version that works with MeMenu?

---

### Post by Dan-Izzard on 2010-05-03
You have to remove Empathy, disable their PPA and clean the cache (sudo apt-get clean && sudo apt-get autoclean and a sudo apt-get autoremove, too). After it, you can re-install Empathy (Empathy 2.30.0.1), go to modify-Preferences-Notify (the second tab) and select the last option)...


Sorry for any error in the language, i'm not english...

---

### Post by paperpill on 2010-05-04
Could you please explain the procedure a little more newbie friendly, cause i've been searching the solution on this problem and this is the first thread that actually solves it.

ty

---

### Post by paperpill on 2010-05-04
> **splatterdash said:**
> I'm on 10.04.

I was curious to see the new features implemented (mainly geo-location) in Empathy, so I added their PPA and did an update. After updating, the notifications for Empathy become separated from the MeMenu (separate icons, no 'Chat' option is specified when I click the MeMenu), although I can still update my status by clicking on my user name.

Does anyone know how to integrate the new Empathy back into MeMenu? If not, how can I roll back to the previous Empathy version that works with MeMenu?

Well sorry for the double post, but after some research i mananged to make it.
It's exactly as Dan-Izzard says.

Remove Empathy from Ubuntu software center
Get ppa-purge and type 
> [SIZE=3][SIZE=3][FONT=arial] sudo ppa-purge [/FONT][/SIZE][SIZE=2]ppa:telepathy/ppa[/SIZE][/SIZE]

This will remove the latest update that bugs with the indicator applet.

The rest is as Dan-Izzard says

---

### Post by nomnex on 2010-05-28
Are you sure?

```
user@pc:~$ sudo ppa-purge ppa:telepathy/ppa
sudo: ppa-purge: command not found
```EDIT: maybe it would be worth mentioning "ppa-purge" has to be installed [1]

[1] [http://preview.tinyurl.com/y92unop](http://preview.tinyurl.com/y92unop)

---

### Post by cfalzone on 2010-06-29
Is anyone savvy as to why the new version doesn't integrate into the MeMenu?

Perhaps there is some way to integrate it back into the MeMenu?

---

