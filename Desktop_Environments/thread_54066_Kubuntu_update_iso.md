---
title: "Kubuntu update iso"
date: 2005-08-03
forum: Desktop Environments
---

### Post by movies1978 on 2005-08-03
Does anyone have a clue howto build a update cd in order to stay updated. So I can take that cd home and update my kubuntu without dying a money and time death, using my isdn connection?

Best regards 

Mathias

---

### Post by GeneralZod on 2005-08-03
[QUOTE=movies1978]Does anyone have a clue howto build a update cd in order to stay updated. So I can take that cd home and update my kubuntu without dying a money and time death, using my isdn connection?

Best regards 

Mathias[/QUOTE]

If you have a Kubuntu install linked up to broadband somewhere, then this is quite easy: make sure you /etc/apt/sources.list match on your broadband and ISDN machines, then update your broadband machine.  All downloaded updates are stored in /var/cache/apt/archives, so you can burn these and copy (using sudo) into the same directory on your ISDN machine.

I'm not sure how to do this without a Kubuntu (or maybe just debian...?) installation on a broadband connected PC, though :/

---

### Post by movies1978 on 2005-08-03
Thx for the answer GeneralZOD I have no machine, but will try to setup one.

Mathias

---

### Post by GeneralZod on 2005-08-03
[QUOTE=movies1978]Thx for the answer GeneralZOD I have no machine, but will try to setup one.

Mathias[/QUOTE]

Personally, I'd wait and see if someone else provides a better solution; there might be a way of doing it without having another Kubuntu install e.g. by just manually downloading a few files from repositories.

---

