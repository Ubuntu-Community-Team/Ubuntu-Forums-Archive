---
title: "Dual Monitor Selection Not Saving After Reboot"
date: 2012-05-14
forum: Desktop Environments
---

### Post by Matt Lex on 2012-05-14
Every time I boot into Xubuntu, I need to open a terminal and enter "sudo amdcccle", select "multi-display desktop with display(s) 2", and orient my monitors within the Display Manager of amdcccle.

In Ubuntu, this setup would save, and I would have to do this within amdcccle only once, after a new installation of the OS.  However, in Xubuntu, I have to go through this process every time I log in.

How can I make sure this problem stops?

I am running Xubuntu 12.04, and my card is an ATI Radeon HD 4200.  My system is running the fglrx driver (not the post-release updates version, which does not work for me).  I had the same problem when I first switched to Xubuntu 11.10.

Thank you!

---

### Post by roelforg on 2012-05-14
```

sudo aticonfig --initial=dual-head
sudo amdcccle

```
tends to work for me.
(there's a bug that prevents you from launching amdcccle as root from gui, running it with sudo manually works)

---

### Post by Matt Lex on 2012-05-16
Thank you for the response.  I tried your code, but after rebooting, the dual monitor selection still did not save.  I had to go back into amdcccle to select multi-display desktop again.

---

### Post by Intangir on 2012-07-10
i am also having this problem
i did a search and found dozens of posts about this problem and not one working solution yet...

---

### Post by Intangir on 2012-07-10
i just found a solution on another of the posts

after you set it up how you like
for some reason you goto the preferences->monitors (or screen resolution) and have it how you like it there (i changed nothing) and hit apply
it asked if i wanted to keep, i said yes

i restarted it, and it saved!

---

### Post by Intangir on 2012-07-11
ok maybe not..

when i opened a full screen game, first it maximized to the wrong monitor..
2nd when i unfullscreened it, it restored cloned mode...

---

### Post by manco1911 on 2013-05-14
> **Intangir said:**
> i just found a solution on another of the posts

after you set it up how you like
for some reason you goto the preferences->monitors (or screen resolution) and have it how you like it there (i changed nothing) and hit apply
it asked if i wanted to keep, i said yes

i restarted it, and it saved!

This worked for me on Ubuntu 12.04 with repositories drivers. 

Thanks man !

---

