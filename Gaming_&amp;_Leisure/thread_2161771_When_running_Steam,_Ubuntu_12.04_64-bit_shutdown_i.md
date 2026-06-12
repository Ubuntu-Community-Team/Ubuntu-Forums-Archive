---
title: "When running Steam, Ubuntu 12.04 64-bit shutdown issue"
date: 2013-07-11
forum: Gaming &amp; Leisure
---

### Post by kengordo on 2013-07-11
Greetings to all, my first Gaming & Leisure post.  I have Steam running just fine on Ubuntu 12.04 64-bit.  There doesn't seem to be any issue starting Steam, but when I decide to shutdown my machine and Steam is running--it takes two attempts to shut down or restart machine.  I have hibernate enabled, and that works on first attempt every time.  What I have noticed is that Steam shuts down on the first attempt.  I can wait to see if anything else is closing, but after an hour, only the Steam process has stopped (on the first attempt).  Once Steam has closed, I can shut down (or restart).  If I don't run Steam in a session, I can shut down or restart on the first attempt, every time.  I can also shut down or restart on first attempt if I exit Steam first.  Has anyone else experienced this?

---

### Post by Rumbl3 on 2013-07-13
I get that i have to shutdown steam before i try to shutdown the computer or restart. It won't do anything at all. No big deal just a extra step to shutdown your rig :)

---

### Post by CatKiller on 2013-07-13
I've experienced the same. I'm guessing that Steam blocks the shutdown process to ensure that it completes its sync, but doesn't release it when it exits.

---

### Post by kengordo on 2013-07-13
> **CatKiller said:**
> I've experienced the same. I'm guessing that Steam blocks the shutdown process to ensure that it completes its sync, but doesn't release it when it exits.

Well I feel better now that it is something that is probably built-in to the Steam client.  Of course sudo reboot always works right away.  I wonder if it is a Unity desktop thing now...

---

### Post by Hexxus on 2013-07-13
Yeah, I've had the exact same issue. Gotta tell it twice, and I agree it does seem to be a Unity desktop thing.

---

### Post by oldrocker99 on 2013-07-14
> **Hexxus said:**
> Yeah, I've had the exact same issue. Gotta tell it twice, and I agree it does seem to be a **Unity** desktop thing.

Which is probably why it's not happened to me.

---

### Post by CatKiller on 2013-07-14
> **oldrocker99 said:**
> Which is probably why it's not happened to me.

I don't use Unity. It could be a Gnome thing, though.

---

### Post by oldrocker99 on 2013-07-14
> **CatKiller said:**
> I don't use Unity. It could be a Gnome thing, though.

Unity is a shell for GNOME, so you're likely right.

---

