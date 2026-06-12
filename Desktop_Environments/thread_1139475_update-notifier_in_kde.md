---
title: "update-notifier in kde"
date: 2009-04-27
forum: Desktop Environments
---

### Post by Zalbor on 2009-04-27
Hello.

I just installed Kubuntu 9.04, where I had 8.10 before. Like I'm used to doing with KDE, I removed its update managers (kpackagekit, update-manager-kde, update-notifier-kde) and added the gnome packages instead (synaptic, update-manager, update-notifier).
I also added update-notifier to the autostart list.

Doing this in 8.10 worked perfectly, and had me using gnome's updaters in kde, complete with the notifier's icon in the system tray whenever updates were available.

In 9.04 however, although updates are currently available (update-manager and synaptic show them) and update-notifier **is** running, no icon appears.

Does anyone know what the problem could be?

---

### Post by eudemus on 2009-08-14
Any joy on this, anyone?

---

### Post by VCoolio on 2009-08-14
The startup command for update-notifier in ubuntu (gnome) is:
```
update-notifier --startup-delay=60
```

maybe the startup-delay is important because it needs to wait for the panel (you do have a notification area on your panel, right?).

---

### Post by eudemus on 2009-08-14
There is a thing called a System Tray, which seems to be where notifications from applications appear, as well as volume control, ethernet connections manager, and so on. That's where I'd expect it to appear.

When running update-manager (with or without the delay) from the command line, I get:

** (update-notifier:8373): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:8373): DEBUG: crashreport_check


???? Any ideas?

Cheers, Eudemus

---

### Post by eudemus on 2009-08-14
Btw, many thanks, VCoolio, for your advice and thoughts on this. It's much appreciated. (Pity the "thank" option has disappeared from these forums.)

Eudemus

---

### Post by eudemus on 2009-08-14
Could this be a solution?

[http://www.mail-archive.com/pkg-kde-talk@lists.alioth.debian.org/msg00470.html](http://www.mail-archive.com/pkg-kde-talk@lists.alioth.debian.org/msg00470.html)

Does that change anything other than how update-notifier is autostarted? (i.e. perhaps this won't solve whatever is the problem leading to the crash when I start u-n from the command line ....?)

Any thoughts?

---

### Post by eudemus on 2009-08-14
Another question (and let me further expose my ignorance) ... 

Is it possible that the "error" messages pasted above are simply the successful output of update-notifier checking for updates (there are 0 updates, of which 0 are security updates) adn for some kind of crash (perhaps the message simply records that it has completed such a check)?

So, perhaps nothing is wrong? And I might expect update-notifier to pop up correctly in my system tray once there are actually some updates for it to announce?

Is that too optimistic?

---

