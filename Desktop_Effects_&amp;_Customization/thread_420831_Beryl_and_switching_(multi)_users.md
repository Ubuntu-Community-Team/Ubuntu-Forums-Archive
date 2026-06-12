---
title: "Beryl and switching (multi) users"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by narnie on 2007-04-24
I was logged into my account on Ubuntu edgy and was amazing my kids with Beryl.

I then switch user to their account and bravely entered beryl-manager into the session/startup.

Then I run beryl-manager. Perhaps you already know what happened. A blank screen crashing the gdm. I tried to log into their account in the "safe mode'  but it still crashed. After snooping around, I found where their autostart was stored and edited beryl out of there and was able to get them back on.

I shut down beryl on my session and was able to then start it on theirs.

So my question:

Is it possible to run beryl in multi-user mode without having to switch it on and off on a per-user basis?

This could be really bad if I'm still logged on and using beryl, and they log on and try to run it.

It would be really sad if on a multiuser environment like Linux if beryl cannot be run be several users at the same time.

If it is possible, I would really appreciate help in setting it up. I've searched and can find this elsewhere on the forum.

Thanks,
narnie

---

### Post by reclusivemonkey on 2007-04-24
I don't think what you want is possible just yet. Please remember Beryl is at version ***[SIZE="3"]0.2[/SIZE]***

---

### Post by p_schott on 2007-05-21
Sorry for double posting.

---

### Post by p_schott on 2007-05-21
It is not only a Beryl related problem, it looks like 3D acceleration doesn't work for multiusers : I have the same problem with google-earth and even some 3D screensavers : hardware acceleration does only work for the first logged in user.

---

### Post by narnie on 2007-05-23
Then this should really be addressed at this level. It really stinks that Windoz can use accel in multiuser mode and we can't. This isn't a good place to be as we try to spread the goodness of Linux.

---

### Post by p_schott on 2007-08-31
I opened a bug report : [https://bugs.launchpad.net/bugs/134448]("https://bugs.launchpad.net/bugs/134448")

---

