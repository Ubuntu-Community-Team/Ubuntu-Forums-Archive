---
title: "XGL/Compiz customisation"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-07
I followed an excellent guide [HERE]("http://tazforum.thetazzone.com/viewtopic.php?t=2189") which got xgl/compiz up and running on my ATI mobility x700 without any deviation.  However, now that I have it set up and running nicely, I want to customise it.  For example, I really don't like the wobbly menus from a usability perspective and want to get rid of them, whilst having other bits and pieces!  I am sure I can remember, from a previous failed attempt, ways of saying what bits you want on and what you want off, but I can not remember how.  A pointer in the right direction would be good, particularly if there is a nice GUI interface for it.

---

### Post by zerwas on 2006-07-07
Hi,

A GUI for compiz:
```
sudo apt-get install gset-compiz
```

Greetings,
zerwas

---

### Post by mcduck on 2006-07-07
> **zerwas said:**
> Hi,

A GUI for compiz:
```
sudo apt-get install gset-compiz
```

Greetings,
zerwas

or use the Configuration Editor (should be in Applications/accssories, if not, start it by running 'gconf-editor' in terminal)

Then browse to apps/compiz and there you ave all available options. 

gset-compiz is also nice, but it's not always up to date with new features in Compiz.

---

### Post by Lunar_Lamp on 2006-07-07
Thanks.

The only problem I am having with compiz is with Kopete - IMs won't stop flashing in the system tray when I have read messages.  Very frustrating.

---

