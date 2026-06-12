---
title: "Green Running Man (gnome panel)"
date: 2007-12-25
forum: Desktop Environments
---

### Post by Xswitch on 2007-12-25
When I upgraded to Gutsy, I had a /home partition set up.  The upgrade went fine and then I updated my **/etc/fstab** to make sda3 my **/home**.

Everything worked perfectly.

**The problem is that my gnome panel is the same one that I had when running Feisty.  The icons are the same.  I don't get the little green running man or any of the other updated icons.  How can I fix this?**

---

### Post by Tenken on 2007-12-26
Your panel layout is stored in your /home folder, so instead of using the default Gutsy setup, Gnome is using your old configuration file. You can either delete your old config file (it's under ~/.gnome2 somewhere) or you could manually add/remove the items.

---

### Post by daengbo on 2007-12-27
You can visit System -> Preferences -> Appearance and change the theme. Click the Customize button to choose the Human icon theme and you should be OK.

---

### Post by Xswitch on 2007-12-28
Thanks Tenken and daengbo...  I went to System > Preferences > Appearance.  I left the Theme alone and clicked on Customize...  I went to Icons and cliked on Mist and Voila, my panel Icons changed....  I now have the Green Running man....  :)  Thanks again...

---

### Post by daengbo on 2007-12-30
Please mark the thread [solved]

---

