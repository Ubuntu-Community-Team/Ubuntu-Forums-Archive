---
title: "GDM2 toolbar randomly chooses top or bottom of screen"
date: 2010-07-10
forum: Desktop Environments
---

### Post by jgo2la on 2010-07-10
GDM2 is doing something very weird on my Ubuntu Lucid install. It occasionally decides randomly to put the toolbar (with keyboard layouts, the time and date, shutdown options, and so forth) at the top of the screen when it appears. I think it's always supposed to be at the bottom of the screen. Why is this happening?

---

### Post by bobcollard on 2010-07-11
> **jgo2la said:**
> GDM2 is doing something very weird on my Ubuntu Lucid install. It occasionally decides randomly to put the toolbar (with keyboard layouts, the time and date, shutdown options, and so forth) at the top of the screen when it appears. I think it's always supposed to be at the bottom of the screen. Why is this happening?
Do you have two or more Workspaces that may be set up differently?  I've seen this happen when the workspaces are inadvertently changed.

---

### Post by jgo2la on 2010-07-11
> **bobcollard said:**
> Do you have two or more Workspaces that may be set up differently?  I've seen this happen when the workspaces are inadvertently changed.

I do use multiple workspaces as well as Compiz. Could you please explain further how that could cause what I'm seeing?

---

### Post by bobcollard on 2010-07-11
> **jgo2la said:**
> I do use multiple workspaces as well as Compiz. Could you please explain further how that could cause what I'm seeing?
Check each of your workspaces to see if any of them has a setting with the panel on top.  If you find it then change the settings for panel in that workspace.  I'm not sure how Compiz effects your panels, I don't use it.  Somethng like this also happens in KDE desktop with different screen settings.  I'm not using Gnome so I can't say for sure, in my Xfce desktop I keep to one workspace and open several programs to use them from the Panel.  A different type of Power user.

---

### Post by jgo2la on 2010-07-11
> **bobcollard said:**
> Check each of your workspaces to see if any of them has a setting with the panel on top.  If you find it then change the settings for panel in that workspace.  I'm not sure how Compiz effects your panels, I don't use it.  Somethng like this also happens in KDE desktop with different screen settings.  I'm not using Gnome so I can't say for sure, in my Xfce desktop I keep to one workspace and open several programs to use them from the Panel.  A different type of Power user.

Just to clarify, I'm referring to the GDM login screen, not the GNOME desktop itself. My different workspaces don't have anything particularly unusual going on.

---

### Post by bobcollard on 2010-07-11
> **jgo2la said:**
> Just to clarify, I'm referring to the GDM login screen, not the GNOME desktop itself. My different workspaces don't have anything particularly unusual going on.
That could be Plymouth messing things up.  Know little about that, sorry.

---

### Post by jgo2la on 2010-07-11
> **bobcollard said:**
> That could be Plymouth messing things up.  Know little about that, sorry.

That I wouldn't doubt. I only recently got Plymouth to display at the proper resolution, without weird green corruption on the graphics, with my proprietary graphics driver.

---

