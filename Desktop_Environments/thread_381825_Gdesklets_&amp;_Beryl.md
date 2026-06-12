---
title: "Gdesklets &amp; Beryl"
date: 2007-03-11
forum: Desktop Environments
---

### Post by progrockusa on 2007-03-11
Hi i've got my system setup so Beryl and Gdesklets both start up.
It appears when beryl kicks in during the start up that it shuts gdesklets down. any way these two can bootup in harmony?

---

### Post by qamelian on 2007-03-11
> **progrockusa said:**
> Hi i've got my system setup so Beryl and Gdesklets both start up.
It appears when beryl kicks in during the start up that it shuts gdesklets down. any way these two can bootup in harmony?

I haven't this problem. Both work together on startup just fine on both my Edgy desktop and my Feisty laptop.

---

### Post by jongkind on 2007-03-11
Instead of starting desklets & Beryl-Manager seperately I use the script below. 

#! /bin/bash
gdesklets start &
sleep 15
beryl-manager

---

### Post by jimbo99 on 2007-03-11
I believe Beryl has a special layer for desklet type apps.  Check to see if it is on.  Move your mouse pointer to the upper left corner of your screen.

---

