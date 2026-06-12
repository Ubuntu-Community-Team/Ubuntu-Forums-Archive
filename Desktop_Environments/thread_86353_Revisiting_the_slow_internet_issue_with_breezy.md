---
title: "Revisiting the slow internet issue with breezy"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Wally on 2005-11-04
Problem: Slow internet and BitTorrent downloads.
I connect to bellsouth dsl lite (max 256k down) via a Wirespeed dsl modem.  When booting with my hoary hard drive, downloads run at a good clip.  In breezy if I do an update from a repository, download a file via firefox or download a torrent, the best I can get is around 20kbs.
ipv6 inFirefox and /etc/modprobe.d/aliases has been turned off.
Speakeasy.com reports better than 200kbs download and better than 100kbs upload.  

What am I missing?

---

### Post by adwait on 2005-11-04
You are confused between 20 kb/s and 200 kbps. 200 kbps = 25kb/s. The speed that you are getting is certainly lower than this, but that could be because of the phone line etc...

---

### Post by Wally on 2005-11-05
I can feel a tickle in my head that I've made this mistake before.
Is it something like kB/s meaning kiloByte/sec and kb/s meaning kilobit/sec?
That's alot of heavy memory digging this early in the morning.

---

### Post by Remmelas on 2005-11-05
[QUOTE=Wally]I can feel a tickle in my head that I've made this mistake before.
Is it something like kB/s meaning kiloByte/sec and kb/s meaning kilobit/sec?
That's alot of heavy memory digging this early in the morning.[/QUOTE]
you are dead on.  Most browsers report kiloBytes/sec, but phone companies measure speeds in kilobits per second.  Two things have to be taken into account when looking at your speeds.  There are 8 bits in a byte, and there is always a certain amount of 'network overhead' as well.

---

