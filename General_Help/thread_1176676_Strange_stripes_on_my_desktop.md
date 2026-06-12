---
title: "Strange stripes on my desktop"
date: 2009-06-02
forum: General Help
---

### Post by chinaski on 2009-06-02
I have what I think is an issue

All items I see on my screen, wether it's desktop icons or text lines on web pages, have strange stripes on their right

Here's a screenshot for better understanding (please enlarge):

[[IMG]http://img189.imageshack.us/img189/450/stripesm.th.png[/IMG]]("http://img189.imageshack.us/my.php?image=stripesm.png")

And here's my video card specs:

```
chinaski@central:~$ sudo lshw -C Video
  *-display               
       description: VGA compatible controller
       product: GeForce 8400 GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
chinaski@central:~$
```I searched before posting but I found nothing

I hope there is a fix for this as it is terribly annoying

Cheers,
Cris

---

### Post by chinaski on 2009-06-02
sorry I forgot to add I use nVdia drivers (version 180) wich I installed thinking it might solve the problem but as you can see it did not

---

### Post by chinaski on 2009-06-03
Bump :(

---

### Post by bacardiandwatermelon on 2009-06-03
It must be my eyes.. I can't see it?

---

### Post by Fzang on 2009-06-03
Sorry, but I can't spot those stripes either

Maybe mark them with a red ring or something? Do they appear on screenshots?

---

### Post by chinaski on 2009-06-03
ok no wonder you cannot see a thing...

...I am an idiot :O

it turned out to be the vga cable that nedeed to be connected properly

it must have been disturbed during house keeping sessions

sorry for opening a useless thread

---

