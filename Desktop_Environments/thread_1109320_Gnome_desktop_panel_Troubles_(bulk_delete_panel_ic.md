---
title: "Gnome desktop panel Troubles (bulk delete panel icons?)"
date: 2009-03-28
forum: Desktop Environments
---

### Post by rexmo on 2009-03-28
I fell asleep on my keyboard last night and when I awoke there were thousands of "accessory" icons in my panel.  I have maunally deleted hundreds, enough to run my browser, but thre are THOUSANDS more to delete.

Is there a way to edit a config file to remove these?  Or a method to BULK delete the extra icons?  They suck up a LARGE amount of memory!

Thank you all!

Ubuntu 8.10 i386

---

### Post by UbuntuNerd on 2009-03-28
go to the terminal and type this command to restore your panels to their default settings:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by rexmo on 2009-03-28
Thanks Nerd!  This cleared out ALL the new things in the bar.

I am back in biz. now!

Thanks

---

