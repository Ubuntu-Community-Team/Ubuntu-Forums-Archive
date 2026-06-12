---
title: "Kubuntu login screen reappears after lgging in, sort of X server restarts"
date: 2009-06-03
forum: Desktop Environments
---

### Post by neo_ritz on 2009-06-03
When I log into Kubuntu, the X server restarts and I'm back on the logon screen.
This happened after an abrupt shutdown during a major upgrade, from Intrepid to Jaunty.
I ran the dpkg reconfigure option from the recovery mode, but that did not solve the problem.
Ho do I combat this situation?

---

### Post by McNils on 2009-06-04
I think that something in your .kde directory is broken. Rename it and restart x. All your settings is removed but you can restore them later...

```
mv -i .kde kde.bak
```

---

### Post by neo_ritz on 2009-06-04
Thanks,I ran all recover menu utilities and it's up and running.
Actually, my bro added karmic repos, and it updated to KDE 4.3 Beta, hus the probs.

---

### Post by ctav01 on 2009-06-13
Sorry, having the same problem.  I tried the 

```
mv -i .kde kde.bak
```and restarted but nothing changed.  It wasn't specified if it should be done in /root or in /home/me so I did both.

I also ran the dpkg reconfigure option from the recovery mode and it did nothing for me too.

neo_ritz, where are these other recovery menu utilities you ran?  If you mean fsck, I tried running that and it gave me a big don't-do-on-a-mounted-system error that scared me off.

Thanks.

---

### Post by ctav01 on 2009-06-14
Turns out I had run out of free space on the drive so nothing was working until I deleted some files.  After that, I'm guessing one of the suggested fixes worked but I have no idea which one it was.

Fixed.

---

### Post by jorgecota on 2010-06-20
Same problem here. I've created 2 new users to keep using kubuntu. These profiles are stuck in the login screen. 
I tried all suggestions, no success yet. Any comments or guide would be appreciated.

---

