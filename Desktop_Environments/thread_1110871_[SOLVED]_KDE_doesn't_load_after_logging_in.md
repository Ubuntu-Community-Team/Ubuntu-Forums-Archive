---
title: "[SOLVED] KDE doesn't load after logging in"
date: 2009-03-30
forum: Desktop Environments
---

### Post by Ubuntiac on 2009-03-30
Does this sound familiar?...

[LIST=1]
[*]You're on Kubuntu Jaunty and...
[*]Things were working OK until recently when you did an upgrade and...
[*]Now you can get to the login screen ok, but...
[*]When you enter your password and hit enter...
[/LIST]

The KDE "loading screen" (with the icons fading in) never comes up! The cursor still works and the background's there, but nothing else happens?! huh?!!!

I've found a bunch of people with this while trying to figure it out on my machine, and we just cracked it! somewhere in the updates kdebase-workspace-bin was removed. Install it again and everything works. To do this just enter in a console (you can get one with ctrl+alt+f1):

```
sudo apt-get install kubuntu-desktop
```

and then go and log in.

Woo hoo! I'm a happy man, now. :KS:popcorn::KS

Hope this helps someone! Kudo's to Jabba_ and DaSkreech from #kubuntu for help with this!

---

### Post by SESF0908 on 2009-03-30
it's too late, if i see this sooner and... I've just reinstalled may computer:shock::shock::shock::shock::shock::shock:. Thanks any way.

---

### Post by Ubuntiac on 2009-08-09
Just had this again on Karmic. Solution (install kubuntu-desktop) worked just as well. Bumping for anyone else getting this.

---

### Post by infomissing123 on 2012-08-10
Thank you so much for posting the solution.  This is exactly what happened to me and your answer helped greatly.

---

