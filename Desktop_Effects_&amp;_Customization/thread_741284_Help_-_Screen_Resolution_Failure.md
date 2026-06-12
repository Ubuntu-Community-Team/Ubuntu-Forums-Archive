---
title: "Help - Screen Resolution Failure"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by Sozin on 2008-03-31
Hi all,

As is often the case, my problem arises from me trying to tweak things early in the morning.

I run linux mint (essentially 7.10) on a toshiba tecra. I decided the screen was a little bright and had a look to see if i could change it. In my poking around, i changed the screen from the generic "plug n play" to have a look at the supported toshiba screens. when i returned to plug n play in the generic screens, all choices of resolution had disappeared bar 640x480.

Nothing i seem to do can get back my beloved 1680x1050 display :(

Does anyone have any ideas?

Thank you,
Ben

---

### Post by vol_freak on 2008-03-31
The same thing happened to me when I was poking around with different driver options. I'm far from a linux expert but this worked for me:

```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by Sozin on 2008-03-31
So did u just follow the prompts and choose card type etc?

Cheers

---

### Post by Sozin on 2008-03-31
PS: Friendly tip for anyone reading this, BACKUP!! Last time I had computer troubles I lost several weeks worth of work which was due a few days later, its not worth the risk...

---

### Post by vol_freak on 2008-04-01
Sorry, this is actually what I used to autoconfigure the video back to what it originally was without having to manually go through each setting. 

```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

---

