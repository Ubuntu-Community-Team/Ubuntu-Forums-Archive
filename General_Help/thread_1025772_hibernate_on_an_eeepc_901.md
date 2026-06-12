---
title: "hibernate on an eeepc 901"
date: 2008-12-30
forum: General Help
---

### Post by jule_ on 2008-12-30
I am using Eeebuntu 2.0 (which is based on Ubuntu 8.10) on an Asus eeepc 901.

Is there any way to integrate or activate an hibernation-mode with this distribution? When I click on the shutdown-button the only three options I get are *shutdown*, *restart* and *suspend*.

It's kind of useless to have a netbook without hibernation option. :(

Thanks for the helping a Linux newbie :)

---

### Post by redilyn on 2008-12-30
Press ALT+F2 and type gconf-editor

Then browse to:

Apps-> Gnome-Power-Manager-> General

Make sure Can_Hibernate is checked.

I should mention that on my eeepc 900HA with eeebuntu 2.0 it is only a difference of 2-3 seconds between hibernation and cold booting. Just something to consider.

---

### Post by snowpine on 2008-12-30
Try clicking on the Power Manager icon in the system tray... you should see a hibernate option there. Also make sure that you have a swap partition that's bigger than your ram. :)

---

### Post by jule_ on 2008-12-31
Thanks for the help. It all worked and now I can use the hibernate mode.

redilyn: You were right, it takes almost the same time to cold boot and to wake up from hibernation. But at hibernation all the previously opened programs and windows remain as they were on wake up.

More questions will come :D

Happy new year! \\:D/

---

