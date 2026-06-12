---
title: "How do I boot rescue mode"
date: 2009-05-01
forum: General Help
---

### Post by FelixTheBat on 2009-05-01
> boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot

If later on you want to try compiz you can install it with Synaptic. As of today compiz still freezes my pc. The "official" fix is blacklisting some graphics hardware so that compiz won't start.

Jerry

p.s. might help if you listed your hardware

I kinda don't understand what he is telling me to do. I got that from another post. Could someone please clear this up for me thanks!

---

### Post by nothingspecial on 2009-05-01
Reboot and when the screen goes black and says "Grub loading" hit Esc and choose recovery mode from the menu.

You could always just turn compiz off

```
metacity --replace
```

---

### Post by FelixTheBat on 2009-05-01
> **nothingspecial said:**
> Reboot and when the screen goes black and says "Grub loading" hit Esc and choose recovery mode from the menu.

You could always just turn compiz off

```
metacity --replace
```

Thanks!

---

