---
title: "Installing KDE 4 and removing KDE 3"
date: 2008-01-11
forum: Desktop Environments
---

### Post by zacattack on 2008-01-11
I have installed KDE4 this morning and I like it.  I was wondering if it was possible to remove KDE 3 completely and just use KDE 4.

---

### Post by limbourg31 on 2008-01-11
sudo apt-get remove kde
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install kde

---

### Post by tmth on 2008-01-11
Yes, i would also like to get rid of KDE3 completely to replace with KDE4, because having KDE3 programs all over the place like old Kate is really getting in the way.

However, above commands do not do anything.

I am wondering though, Kubuntu is very heavily built on top of KDE3 libraries.  In fact, if you go to somewhere like Adapt in while KDE4 and then about->kde, it returns 3.5.8 .  So perhaps gutsy can't function on anything besides that...

If that assumption is wrong, i would really like to get rid of KDE3 stuff.

---

### Post by Bill Cosby on 2008-01-12
I am not sure, but it seemed to be too much of a hssle to get rif oall the old stuff.
I just did a fresh new install, and installed a command line system, after that, I added the kde4 repos, and installed xorg and kde4-core and kdm-kde4, and that's that, then you have an awfully lean system :D
And you should go thorugh the repos and install some basic kde4 packages, like kdemix-kde4, kdewallet-kde4, kuser-kde4, etc.
The thing is, that kde4 has not replacements for all programs, there are actually just a few, so in the end you will end up using old kde3 apps, e.g. like amarok.

I don't recommend to use kde4 right now, it is simply too much of a beta.

---

### Post by tmth on 2008-01-12
That sounds interesting.

When you installed xorg, did it configure everything propperly or you had to configure X manually?

---

### Post by tmth on 2008-01-12
OK, its like i thought.  Some parts of Kubuntu are too heavily based on kde3 libs.  After a very painful process of removing KDE3 and putting on KDE4, when i installed Adept Manager back on it put some kde3 libraries on together with old Konsole.  I think i can live with that.

My problem now is that Plasma crashes every step of the way and i have to start it up through terminal.  There are also a lot of icons missing for many applications.

---

