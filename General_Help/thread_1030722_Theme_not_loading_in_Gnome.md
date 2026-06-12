---
title: "Theme not loading in Gnome"
date: 2009-01-04
forum: General Help
---

### Post by pan69 on 2009-01-04
Hi. I recently upgraded from Hardy to Intrepid and I seem to be having some problems with my theme modifications. 

Every time I do a cold boot (like first thing in the morning) my theme is not loaded properly. Most elements are Gnome defaults, like the task bar and Nautilus looks like a default un-themed Gnome version.

When I logout and log back in it usually loads in properly but sometimes I have to repeat the logout/login process a couple of times.

Any help would be appreciated.

Thanks,
Luke

---

### Post by gettinoriginal on 2009-01-04
Are you running compiz or metacity ??  which ever you are running, type in terminal your choice of these two:
```
metacity --replace
```
```
compiz --replace
```

---

### Post by pan69 on 2009-01-05
Hi. Thanks for that. I think I run metacity but I'm not sure. Is there a way to find out?

I tried to look it up myself and thought it would be mentioned in the preference panel, but when I tried to open it up I got this message:

```

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

```

I never ever touch anything KDE so that shouldn't be the issue.

---

### Post by gettinoriginal on 2009-01-05
Install Compiz Fusion Icon from Synaptic, once it is installed, it will be under applications > system tools, click on it and it will put an icon in your notification area, right click that and it will tell you what you are using for window decorator and window manager.  :P

---

### Post by maybeway36 on 2009-01-05
Seems liek a problem with gnome-settings-daemon. A workaround would be to press Alt+F2 when you log in and type "gnome-settings-daemon" (without quotes) into the box and press Enter.

---

### Post by pan69 on 2009-02-04
Hi guys,

sorry for the late reply. Doing:
```

metacity --replace

```

doesn't do anything (yes, I run metacity).

Starting the gnome-settings-daemon fixes the problem for the current login but it doesn't solve the problem permanently. Is there a way to make this problem go away for good?

Thanks,
Luke

---

