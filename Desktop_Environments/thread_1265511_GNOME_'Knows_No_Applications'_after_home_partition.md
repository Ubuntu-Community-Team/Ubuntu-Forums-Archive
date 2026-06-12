---
title: "GNOME 'Knows No Applications' after home partition filled up"
date: 2009-09-13
forum: Desktop Environments
---

### Post by stderr on 2009-09-13
When I click "Applications" on the top panel under GNOME, no menu appears, although the "Applications" option becomes selected. Places and System still work fine. My second "Menu Bar" on the panel (which normally shows all 3 in one when clicked) presents only the Places and System options, no Applications entry.

This began when I allowed my home partition to fill to 100%. Upon freeing space on the partition, the situation wasn't resolved, and following a reboot, nothing's changed. 

Furthermore, right clicking the menu and choosing Edit Menus no longer launches the menu editor app (can't remember its name), and Alt+F2's list of known applications is now blank. 

Any ideas? Is there a command I can use to rebuild the list somehow?

```

ace@ace1:~$ df -hl | grep home
/dev/sda3              92G   86G  1.9G  98% /home

```

---

### Post by stderr on 2009-09-13
Fix here: [http://ubuntuforums.org/showthread.php?t=541503]("http://ubuntuforums.org/showthread.php?t=541503")

To summarise, ~/.config/menus/application.menu was empty. 
A general copy (non-customised for your user) exists at /etc/xdg/menus/application.menu and you can copy that over the blank copy in your user directory. Any customisations you made to your menu are lost, but everything works again. No reboot is required.

```

cp /etc/xdg/menus/application.menu ~/.config/menus/application.menu

```

---

### Post by rahul_bhise on 2012-08-05
thanks stderr
that solved my problem in ubuntu 12.04

---

