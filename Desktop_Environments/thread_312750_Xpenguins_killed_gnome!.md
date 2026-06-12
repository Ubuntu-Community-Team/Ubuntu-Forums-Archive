---
title: "Xpenguins killed gnome!"
date: 2006-12-04
forum: Desktop Environments
---

### Post by darundal on 2006-12-04
I am running Dapper 6.06. I recently installed the x-penguins package (adds a panel applet that basically makes little penguin deskbuddies do stuff) and when I added it to the panel gnome just stopped working. It complained about the tomboy panel item, then refused to run altogether. Anyone know what config I need to change to fix it so it doesn't try to run the penguin applet ? Thanks!

---

### Post by gil_smos on 2006-12-25
Hey, I just got the same thing. Did anyone ever solve that?

Thanks,

Gil

---

### Post by geek_Man on 2006-12-25
I had that problem too, but I fixed it. Open the System Monitor and kill the Xpenguins applet. It'll pop up a window asking whether it should delete something, click yes, the gnome-panel should restart and you're good to go. Hope this helps and merry Christmas!

---

### Post by gil_smos on 2006-12-25
Thanks for the quick response, but how do I get the system monitor working if the panel is not working?

---

### Post by geek_Man on 2006-12-25
Open Nautilus and navigate to /usr/share/applications/System Monitor.

---

### Post by macogw on 2006-12-26
I went with adding a launcher that runs xpenguins to the panel instead of using the xpenguins applet.

---

### Post by gil_smos on 2006-12-26
Cool, I'll give it a shot, and let you know how it went.
Thanks a lot.

---

### Post by gil_smos on 2006-12-28
Yeah man! Worked like a charm!
Thanks a lot.

---

### Post by robenroute on 2007-03-12
> **darundal said:**
> I am running Dapper 6.06. I recently installed the x-penguins package....

Not just Dapper, Edgy also gets very edgy ( ;) )when installing the applet. If you're not comfortable with the command line, under [SIZE="4"]***no***[/SIZE] circumstances install the applet!

Ta

---

### Post by Mr_bleu on 2007-06-05
It killed my fiesty version of gnome also.  I was VERY upset after trying to get gnome/gnome failsafe to work.  I started an xcfe session, right clicked on the desktop to get a menu, and went to synaptic manager to uninstall it. Rebooted into gnome and the session's fine now.

---

