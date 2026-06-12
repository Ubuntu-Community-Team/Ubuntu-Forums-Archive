---
title: "[B]Boot in to command line[/B]"
date: 2006-09-27
forum: Desktop Environments
---

### Post by fernando_lopes_jr on 2006-09-27
I want to setup a Ubuntu server but don't need for it to boot up Gnome always how can I make it just boot to command line and enter gnome when I need it.

---

### Post by henriquemaia on 2006-09-27
> **fernando_lopes_jr said:**
> I want to setup a Ubuntu server but don't need for it to boot up Gnome always how can I make it just boot to command line and enter gnome when I need it.


Just turn the init script **gdm** off. You'll get a nice command line when booting.

---

### Post by fernando_lopes_jr on 2006-09-28
Could you give me the exact comand to do that please

---

### Post by henriquemaia on 2006-09-29
If you have BUM  (boot-up manager) installed, you can choose to have the gdm service turned of. BUM is a gui for doing that.

Or you can install sysvconfig, an utility to do the same thing, but on cli - with menus and very easy to use.

On both you just have to turn gdm off.

---

