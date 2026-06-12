---
title: "Administrative tasks need to be started twice"
date: 2008-03-11
forum: Desktop Environments
---

### Post by drocra on 2008-03-11
I'm having a very odd problem while attempting to run administrator tasks in GNOME (I'm in Ubuntu 7.10 with all updates, plus Compiz).

Every time I try to run an administrative task that requires a pop-up password, I have to try starting the program twice before it will bring that popup box up. 

For example, if I start synaptic, it will show a window in the taskbar that says "Starting Administrative Application". But instead of bringing up the password box, it just sits there for a while, and eventually disappears. Clicking on it does nothing.

If I try it again, however, it brings up the password box no problem. It's only the first time.

Much searching and it doesn't seem like anyone else is having this problem...

I'd really prefer not to do a fresh install; does anyone have any ideas?

---

### Post by Herr Otto on 2008-03-15
Hi there,

I had the same problem until yesterday, now it got even worse; the Administrative tasks won't get though at all anymore (before, it was starting sometimes, or after trying twice). So none of the applications that require admin rights will start now.

I've also noticed, and I assume (but I'm not sure) these things are related, that when starting a command line task with sudo, the command line comes back with ```
sudo: unable to resolve host ubuntu
```.

I've checked ```
/etc/hostname
``` for problems but there the hostname was a single word, ubuntu, so that seems correct to me too.

Any ideas? This is getting quite tedious and it's hard to fix anything without admin rights!

ciao Otto

---

### Post by Elotero on 2008-03-22
> **Herr Otto said:**
> Hi there,

I had the same problem until yesterday, now it got even worse; the Administrative tasks won't get though at all anymore (before, it was starting sometimes, or after trying twice). So none of the applications that require admin rights will start now.

I've also noticed, and I assume (but I'm not sure) these things are related, that when starting a command line task with sudo, the command line comes back with ```
sudo: unable to resolve host ubuntu
```.

I've checked ```
/etc/hostname
``` for problems but there the hostname was a single word, ubuntu, so that seems correct to me too.

Any ideas? This is getting quite tedious and it's hard to fix anything without admin rights!

ciao Otto

same exact problem... can anyone help?

hardy alpha 5

---

### Post by agent8131 on 2008-04-24
See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

---

