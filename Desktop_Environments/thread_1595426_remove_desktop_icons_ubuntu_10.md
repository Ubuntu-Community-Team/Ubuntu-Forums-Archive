---
title: "remove desktop icons ubuntu 10"
date: 2010-10-13
forum: Desktop Environments
---

### Post by True_Snake on 2010-10-13
Hello fellow ubuntu'ers,

I'd like to remove the icons of my connected drives from my desktop,
I've found some threads about it but nothing that seems to work for me on Ubuntu 10.
Can someone give me a simple how-to to achieve this.

thx in advance for the help

---

### Post by JustinR on 2010-10-13
> **True_Snake said:**
> Hello fellow ubuntu'ers,

I'd like to remove the icons of my connected drives from my desktop,
I've found some threads about it but nothing that seems to work for me on Ubuntu 10.
Can someone give me a simple how-to to achieve this.

thx in advance for the help

Hi,

Press 'ALT + F2'
Type in 'gconf-editor'
In 'gconf-editor' navigate to: '/apps/nautilus/desktop'
Find the key called 'volumes_visible' and uncheck the box. 

Now you shouldn't see any mounted drives on your desktop.
Log out and Log back in if nothing happens.

---

### Post by True_Snake on 2010-10-13
worked perfectly, all icons are gone

thank you,
I'm going to mark this thread solved

---

