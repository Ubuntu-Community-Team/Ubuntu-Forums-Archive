---
title: "panels has crashed"
date: 2010-03-12
forum: Desktop Environments
---

### Post by toronado on 2010-03-12
Panels has crashed (all panels blank and non responsive - unable to right click on panels - nothing happens) and problem persists after reboot. Is there a way to fix?
Ubuntu 9.10

---

### Post by drpjkurian on 2010-03-12
Hi
Delete the panel and create a new panel. It might solve the issue

---

### Post by toronado on 2010-03-12
> **drpjkurian said:**
> Hi
Delete the panel and create a new panel. It might solve the issue

I cannot right click on the panels. Well, I CAN, but nothing happens. I don't get a context menu. Is there another way to delete the existing non-responsive panels?

---

### Post by antiphatique on 2010-03-12
Hi,
I had a problem with my panels a little while back. My task bar was caught in a loop of trying to remove itself which clogged up my panel accessibility in general. So it is not quite the same as the non-reaction of your panel. But I did find something to set the panels back to default configuration (which solved my problem).  Three easy steps in terminal:

1: gconftool --recursive-unset /apps/panel
2: rm -rf ~/.gconf/apps/panel
3: pkill gnome-panel

Voilà!

Hope this works for you

---

### Post by toronado on 2010-03-13
> **antiphatique said:**
> Hi,
I had a problem with my panels a little while back. My task bar was caught in a loop of trying to remove itself which clogged up my panel accessibility in general. So it is not quite the same as the non-reaction of your panel. But I did find something to set the panels back to default configuration (which solved my problem).  Three easy steps in terminal:

1: gconftool --recursive-unset /apps/panel
2: rm -rf ~/.gconf/apps/panel
3: pkill gnome-panel

Voilà!

Hope this works for you

IT WORKED!

Thank you!!!

Thank goodness for default configs. I actually ran your commands from the recovery mode command prompt because I couldn't even figure out how to launch terminal (or any apps for that matter) from within the GUI without having an apps menu because I'm such a Linux noob!

---

### Post by phillipjennings5 on 2010-03-16
wait thats not working for me i copied and pasted
gconftool --recursive-unset /apps/panel
in the Terminal and i get nothing it just goes back to 
Name@name-laptop:~$
am i missing some sudo command or something

---

