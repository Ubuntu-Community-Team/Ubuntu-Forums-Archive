---
title: "/dev permissions incorrect. Big problem"
date: 2009-04-06
forum: General Help
---

### Post by ShaunG on 2009-04-06
Hey all,

I am hoping someone here can help out with yet another problem.

I recently discovered that certain things were not working because the permissions and ownership of items in /dev/* was off .. way off. A lot of things are owned by dialout that should be owned by root.

Anyways, I went about fixing this by chmodding and chowning my head off. That fixes the problem after some /etc/init.d/whatever start.

However, on reboot, /dev/* permissions and ownerships have become re-borked. 

I am really hoping someone can help with this as it is a rather big problem :(

Thanks in advance

~ Shaun

---

### Post by ShaunG on 2009-04-06
Anyone? I would love to get this sorted soon, or at least find out what to do..or what may be causing this.

---

### Post by snova on 2009-04-06
> **ShaunG said:**
> I recently discovered that certain things were not working because the permissions and ownership of items in /dev/* was off .. way off. A lot of things are owned by dialout that should be owned by root.

What isn't working? You shouldn't have to mess with permissions.

> However, on reboot, /dev/* permissions and ownerships have become re-borked.

That's because these files do not exist. :) They are created every time you boot.

> **ShaunG said:**
> Anyone? I would love to get this sorted soon, or at least find out what to do..or what may be causing this.

It hasn't been that long... you should generally wait at least a day to bump your thread.

Anyway, if you really must change ownership of device files, they are created by the udev system, which is controlled by various configuration files in **/etc/udev/rules.d**. The exact file you need to edit might not be apparent, but the syntax is quite simple.

---

### Post by ShaunG on 2009-04-07
> **snova said:**
> Anyway, if you really must change ownership of device files, they are created by the udev system, which is controlled by various configuration files in **/etc/udev/rules.d**. The exact file you need to edit might not be apparent, but the syntax is quite simple.

Thanks I found the problematic file. Thank you very much. :D

As for bumping after so short a time, I was VERY frustrated and not getting anywhere on my own. After a good night's rest I got it. Thank you though :D

---

