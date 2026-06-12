---
title: "Evolution: minimize to tray on close"
date: 2008-05-29
forum: Desktop Environments
---

### Post by lviggiani on 2008-05-29
Hi,
I recently moved to gnome after one year with kde.
One of the good things kontact has, is the possibility to minimize the program in the system tray when the close button is clicked.
Is it possible to do the same on Evolution?
Thanks.

---

### Post by bobynux on 2008-06-01
Hi,

I don't think that possibility exists in Evolution.
But you can use Alltray.

It'll minimize any application in the systray.

[http://alltray.sourceforge.net/]("http://alltray.sourceforge.net/")
It's available in the repos, so you can easily install it via Synaptic.

---

### Post by iamnotthemessiah on 2008-06-01
if you have a problem with the repo version of alltray try this [https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583](https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583)

---

### Post by lviggiani on 2008-06-03
Thanks!

---

### Post by nowhere@cox.net on 2008-06-07
I'm using the launchpad version of AllTray and it seems it doesn't play nice with Evolution. When launching evolution with all tray, the current new mail notification is forced out of the notification area into it's own window, a window that won't shut down nicely. I have to force a quit on it. 

Perhaps I'm doing something wrong. I launched with 
```
alltray -s -l -na -st evolution --component=mail
```

---

### Post by apche93 on 2008-08-25
actually i found that if u take off the "-na" and make it run w/o the Alltray in window title it runs w/o glitchiness!

so:

```
alltray -s -l -st evolution --component=mail
```


Unless u are really obsessed with the "Alltray" thing being there.. Hey! id rather have it run smoothly than doing extra work any day right? lol

hope that helps

---

### Post by zoomy942 on 2010-04-05
wonder how this might work in 10.04?

---

### Post by lingenfr on 2010-11-21
Yes, unfortunately you can find posts on this issue going back several years. The appropriate behavior is for evolution to 'minimize to tray' on close just like pidgin does with the appropriate plug-in. Then you would be notified of new mail, etc via the existing notification icon. Again, just like pidgin does with the plug-in. Disappointing that there are many, many links in many forums asking for this feature, but years with no progress. Running multiple trays is not the answer.

---

### Post by Dustout on 2010-12-12
I too have been wanting this feature for some time, seems like ubuntu has chat/music/broadcast down pat, but email just doesn't work as nicely

---

### Post by puller on 2010-12-24
I leave Evolution opened in the fourth desktop, it's a poor solution tough.

---

