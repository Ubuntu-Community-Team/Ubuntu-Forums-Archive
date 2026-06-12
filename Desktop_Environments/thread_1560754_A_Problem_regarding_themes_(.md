---
title: "A Problem regarding themes :("
date: 2010-08-25
forum: Desktop Environments
---

### Post by wkhasintha on 2010-08-25
Since of late "Appearance preference" behaves awkwardly . Normaly It is supposed to show themes in /usr/share/themes right? but now it shows themes only in ~/.themes folder. I don't know what affected the change. how do I configure it as to show themes in /usr/share/themes/,? 

also whatever theme I use , Controls would stay same(Classic controls). They wouldn't be update to those of the Theme used.


[IMG]http://i36.tinypic.com/2dgoupv.png[/IMG]

---

### Post by mcduck on 2010-08-25
First thing I'd try is to check if gnome-settings-daemon is running. Just hit Alt-F2 and run "gnome-settings-daemon" to see if that fixes the problem.

Also make sure you have the required GTK2 engines installed for your themes (the one you have currently selected requires the Equinox engine, which is not available in Ubuntu's repositories so you need to install it manually).

---

### Post by wkhasintha on 2010-08-25
> **mcduck said:**
> First thing I'd try is to check if gnome-settings-daemon is running. Just hit Alt-F2 and run "gnome-settings-daemon" to see if that fixes the problem.

Also make sure you have the required GTK2 engines installed for your themes (the one you have currently selected requires the Equinox engine, which is not available in Ubuntu's repositories so you need to install it manually).

Thanx for replying bro.

gnome-settings-daemon is running but no change. Equinox theme engine is present too. Whatever theme I applied (even Ambiance) controls don't change. I reset gnome cofigs too.

[ATTACH]167477[/ATTACH]

---

### Post by wkhasintha on 2010-08-25
:(

---

### Post by wkhasintha on 2010-08-27
Bumpo

---

