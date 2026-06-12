---
title: "Cannot install ubuntu-desktop"
date: 2010-05-16
forum: Desktop Environments
---

### Post by drinkleadsoup on 2010-05-16
I am trying to install ubuntu-desktop through the synaptic or terminal.

Through synaptic, I get a window that says,

[HTML]please insert the disc labeled
 'Ubuntu 10.04 _Lucid Lynx_ - Alpha i386 (20100223.2)'[/HTML]


In the terminal, I get,

[HTML]Media change: please insert the disc labeled
 'Ubuntu 10.04 _Lucid Lynx_ - Alpha i386 (20100223.2)'
in the drive '/cdrom/' and press enter

[/HTML]

I have tried mounting the lucid iso to my /media/cdrom.

My optical drive does not work.

Any other ideas???

---

### Post by drpjkurian on 2010-05-16
Hi
Burn the .iso image to CD and then try.

---

### Post by Dayofswords on 2010-05-16
is the cd turned on in your software sources?

---

### Post by drinkleadsoup on 2010-05-16
my optical drive no longer works.

I am looking for a workaround to make it possible to install the ubuntu-desktop.  

I deleted ubuntu-desktop because of this:

[http://ubuntuforums.org/showthread.php?t=1444672](http://ubuntuforums.org/showthread.php?t=1444672)

Now, I cannot reinstall it.

---

### Post by aysiu on 2010-05-16
How about installing it over the internet instead of off a CD?

---

### Post by kio_http on 2010-05-16
[COLOR=DarkRed]WARNING:
You are using a pre-release version of Ubuntu, please upgrade to the final one.
[/COLOR]

---

### Post by 3rdalbum on 2010-05-16
Go to System > Administration > Software Sources

Toward the bottom of the window there's an entry for your CD. Uncheck it.

Click Close and you'll be asked if you want to reload the package list - you do. Now you can install ubuntu-desktop again from the Internet.

---

### Post by drinkleadsoup on 2010-05-16
3rdalbum is the smartest person in the room.

---

### Post by Dayofswords on 2010-05-17
> **drinkleadsoup said:**
> 3rdalbum is the smartest person in the room.

kinda what i meant in my post =p
i was too lazy to type out the whole thing i meant lol

---

### Post by PJW9779 on 2011-04-23
Sure, but how when you're doing a fresh install on a bare machine?

---

