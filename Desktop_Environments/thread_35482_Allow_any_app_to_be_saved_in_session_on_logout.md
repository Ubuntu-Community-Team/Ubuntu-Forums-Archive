---
title: "Allow any app to be saved in session on logout"
date: 2005-05-19
forum: Desktop Environments
---

### Post by Sam on 2005-05-19
When I logout and save the session, only the "basic" applications (like terminal, nautilus, ...) seems to be saved in the session (there is a dialog box which informs that the other app won't restore on next login).

I would like to have Firefox, Thunderbird, or any application saved in the session. Is there a way to allow this ?

---

### Post by ruben_b on 2005-05-19
you can start the other apps like firefox with the "autostart". just go to:

System > Preferences > Sessions

---

### Post by doclivingston on 2005-05-19
For applications to be saved automatically they need to support gnome-session. Short of the developers of the other applications writing support for it, you'll have to take ruben_b's advice and add it to the list of start-up applications

---

### Post by Sam on 2005-05-19
[QUOTE=doclivingston]For applications to be saved automatically they need to support gnome-session. Short of the developers of the other applications writing support for it, you'll have to take ruben_b's advice and add it to the list of start-up applications[/QUOTE]
This is what I thought... :-?

Thank you both for your advices !

---

### Post by anatole on 2005-08-28
can i define somehow where should gnome place the apps i want to open at startup? i mean, i have a strict workspace layout... xchat and gaim on workspace 1, firefox on workspace 2, xmms and a terminal on workspace 3... is that possible, to have gnome open these apps on the workspace i want?

---

### Post by doclivingston on 2005-08-28
[Devil's Pie](http://www.burtonini.com/blog/computers/devilspie) sounds like what you want, a utility which can perform actions (moving to a different workspace, etc) absed on a set of rules. It should be in universe.

---

