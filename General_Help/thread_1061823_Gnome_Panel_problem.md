---
title: "Gnome Panel problem"
date: 2009-02-06
forum: General Help
---

### Post by Basics102 on 2009-02-06
Fellow Ubunters,

I have an easy but nasty problem that I am having problems with. I was about to customize my panels and instead pressing move I pressed remove from panel and deleted run shortcuts for wlan, battery(its a notebook), you know the standards apps shortcuts. I thought it would be rather easy to restore them to their initial appearance and location but the apps available to add to the panel are not the same and don't seem to have the same look aswell as for icons.

Best Regards

---

### Post by overlord.gaurav on 2009-02-06
I believe you've deleted the notification area.
Right click your panel > Click on Add > now add "Notification Area"

---

### Post by UbuntuNerd on 2009-02-06
by the picture it looks like you're also missing the workspaces at the bottom and the trash can, if the solution provided above doesn't solve your problem type this commands in a terminal to restore your panels to their defaults settings like they were before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

