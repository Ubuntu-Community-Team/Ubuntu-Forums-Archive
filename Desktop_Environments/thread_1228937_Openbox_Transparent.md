---
title: "Openbox Transparent"
date: 2009-08-01
forum: Desktop Environments
---

### Post by nperry on 2009-08-01
Hello guys,

I've just install openbox and the only thing is annoying me is that when I have my terminal app transparent its only transparent to my background and not the window behind. (Image below). Now when I'm logged in using gnome/kde the effect is able to see the app behind. 

[[IMG]http://img198.imageshack.us/img198/3180/screenshotsbv.th.png[/IMG]](http://img198.imageshack.us/i/screenshotsbv.png/)

Anyone got any suggestions what I can have in my autostart so this works.

Thanks

---

### Post by Dullstar on 2009-08-01
At least Openbox works for you.

For me it won't even start.

---

### Post by darthmob on 2009-08-01
I use xcompmgr for basic transparency in openbox. It's not perfect but it gets the job done.

minimal startup is with: xcompmgr -n

---

### Post by urukrama on 2009-08-02
> **nperry said:**
> Anyone got any suggestions what I can have in my autostart so this works.

Thanks

If you want true transparency, you'll need xcompmgr and transset running. Have a look at my Openbox guide (link in signature) to figure out how to set it up.

I hope this helps.

---

### Post by nperry on 2009-08-02
> **urukrama said:**
> If you want true transparency, you'll need xcompmgr and transset running. Have a look at my Openbox guide (link in signature) to figure out how to set it up.

I hope this helps.

Thanks its working great now :) Well on my netbook, can't seem to get it working with nvidia...

---

### Post by urukrama on 2009-08-02
> **nperry said:**
> Thanks its working great now :) Well on my netbook, can't seem to get it working with nvidia...

I'm glad it worked.

I'm afraid I can't help you with nvidia, as I've never used them, but I'm sure you'll find help here or through an internet search. Good luck!

---

### Post by nperry on 2009-08-02
> **urukrama said:**
> I'm glad it worked.

I'm afraid I can't help you with nvidia, as I've never used them, but I'm sure you'll find help here or through an internet search. Good luck!

Managed to get it working, typo'd in xorg.conf.


Great article, thanks!

---

