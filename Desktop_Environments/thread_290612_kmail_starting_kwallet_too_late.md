---
title: "kmail starting kwallet too late"
date: 2006-11-01
forum: Desktop Environments
---

### Post by kkinder on 2006-11-01
I've configured kmail -- in the configuration box and when it prompts me -- to store both my passwords for pop/imap. Unfortunately, every time it starts it asks me for both passwords, THEN asks me for my kwallet password. Subsequent starts of kmail are fine.

Has anyone else noticed this? I don't think kmail works right unless kwallet is already running -- or something like that.

Quite lame.

---

### Post by ltmon on 2006-11-01
There seems to be some gigantic issue with kmail and kwallet in Edgy.  I don't know whether it's due to KDE 3.5.5 or the packaging of Edgy.

I have had all sorts of behaviour, from kwallet+kmail crashing KDE to not storing passwords for kmail at all.  I've not had it working correctly at all since the upgrade.

It's a pretty annoying issue, and a pretty lame one to have given everything else is working out pretty well for me.

Here's hoping someone finds a solution.

L.

---

### Post by kkinder on 2006-11-01
Actually edgy horked up my configuration so badly that I just backed up my data, deleted my user account, and started over. That leads me to where I am now.

---

### Post by ltmon on 2006-11-01
I got some success by running kmail on it's own (alt-f2: kmail) and then entering passwords, and then quitting and starting up kontact.

It now seems that kontact is happy to integrate with kwallet.

---

### Post by tristure on 2006-11-09
It doesn't seem to work on my box. I should add that kwallet is totally dysfunctional on my fresh edgy. It doesn't save any password whatsoever, even in Konqueror or other apps. It seems to work during a session, but whenever I log out and log in again, it seems to have forgotten everything. Really frustrating.

---

### Post by pressman57 on 2006-11-19
I got some success by running kmail on it's own (alt-f2: kmail) and then entering passwords, and then quitting and starting up kontact.

It now seems that kontact is happy to integrate with kwallet.
Reply With Quote

That worked for me until a reboot, then it's back to kwallet

---

