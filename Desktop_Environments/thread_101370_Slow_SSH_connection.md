---
title: "Slow SSH connection"
date: 2005-12-09
forum: Desktop Environments
---

### Post by n!x on 2005-12-09
Hi,

I'm running Irssi on my Ubuntu box (Hoary) and connecting to it from my laptop through SSH from Ubuntu "Breezy Badger". It feels very heavy and slow when I'm connected via Ubuntu -> Ubuntu box but not when I connect from Window XP (PuTTy) -> Ubuntu box. What can be wrong - can it be the Wireless LAN which is slow? If so, then it also should be slow when I connect from Win XP to my Ubuntu box, but it ins't. It's only heavy and slow when I connect from Ubuntu to my Ubuntu box....

Anyone having a suggestion?

/n!x

---

### Post by jdong on 2005-12-09
Try pinging from all the  combinations you mentioned. See any major difference?

---

### Post by kaamos on 2005-12-09
Try ssh without ipv6: "ssh -4 [email]user@ubuntubox.addr[/email]ess".

Another thing you could try is to use firestarter to allow all connections from the Ubuntu box running ssh. This probably won't help because this is an ubuntu-ubuntu connection, but doing this dropped 10 seconds of my login time on ssh to my school server that runs SunOS. The server made checks on port 113 as well as 22.. No idea why.

---

### Post by n!x on 2005-12-09
[QUOTE=jdong]Try pinging from all the  combinations you mentioned. See any major difference?[/QUOTE]

It seems that when I'm pinging my Ubuntu box from my Ubuntu laptop there's som breaks in the sequences - It's running fine the first 20 - 40 pingings (~1.25 - 1.75 ms) but then the next ping is about ~75 - 110 ms. Hmm there is maybe something wrong with my wireless on my Ubuntu box... but what?

---

