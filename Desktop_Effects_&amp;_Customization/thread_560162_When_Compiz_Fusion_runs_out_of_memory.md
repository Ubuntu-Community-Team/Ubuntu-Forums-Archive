---
title: "When Compiz Fusion runs out of memory"
date: 2007-09-26
forum: Desktop Effects &amp; Customization
---

### Post by VictorR on 2007-09-26
I am using Compiz Fusion with NVidia GeForce 4 MX440 card (64 MB video RAM) with Ubuntu Feisty Fawn. Sometimes CF runs out of memory and displays windows with black client area or black menus.

Is there a way to share some system memory with NVidia?

 A built-in S3 chip (now disabled) used shared system memory and BIOS allows do allocate it, but seems it does not work for me.

---

### Post by VictorR on 2007-10-05
I have found some kind of workaround. Just a couple of things which help to reduce video memory consumption.
First, added --indirect-rendering to my Compiz start up command
> compiz --replace **--indirect-rendering** -c emerald

Second, removed cube transparency.

---

