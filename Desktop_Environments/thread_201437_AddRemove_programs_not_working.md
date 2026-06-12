---
title: "Add/Remove programs not working?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Pichu0102 on 2006-06-21
I'm having problems using Add/Remove Programs. I can't install anything, and when I click reload in Synaptic Package Manager, it stays at Checking at an unknown download rate, and it never downloads any new update files.
It was working a little bit ago, and I haven't restarted recently, so what could be wrong?

---

### Post by lindyslack on 2006-06-21
I am not sure if this will help but if it is a bug in Synaptic open up Terminal from Applications > Accessories > Terminal and type 

sudo apt-get update

enter your password:

Then enter...

sudo apt-get upgrade

Assuming it is a problem with Synaptic and not Apt this may fix the problem... Never had the problem but thats the first thing I would try.

Hope it helps!

---

