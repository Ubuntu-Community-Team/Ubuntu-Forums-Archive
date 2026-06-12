---
title: "Gwibber no theme integration and bad notifications."
date: 2011-11-16
forum: Desktop Environments
---

### Post by grusty on 2011-11-16
I just install xubuntu 11.10. I knew this system, is awsome.

I install gwibber, but gwibber (and Ubuntu Software Center-USC-) have not a theme integration with xfce themes. Is not a problem with USC, but gwibber have a very ugly face, like win3.1.

And, every 5 minutes check the actualizations, but all noifications windows (the black small ones) appear at same times in all screen, an dissapeer in 2 seconds, is not possible read 5 or 10 notifications at same times, What can I do?

---

### Post by cottfcfan on 2011-11-16
This is a common problem, now that many apps are GTK3, or QT.
Gwibber is a GTK3 app, so does not integrate with a GTK2 theme.
What you need to do is install a GTK3 theme from here:
[http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=e102a845e5fe54f2348e397f3c3f6ebd](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=e102a845e5fe54f2348e397f3c3f6ebd)
I use the Ambiance blue one.
It needs extracting to /usr/share/themes as root.
If the apps are QT Apps you need to install libgnomeui-0 from synaptic.
That should resolve all your integration problems.

---

### Post by grusty on 2011-11-16
Excellent cottfcfan, you are right, is a problem about gtk2(gtk3 integration, I hawe not idea.

Thanks, in the issue of themes is solved for me. Thanks.

---

### Post by grusty on 2011-11-16
How I change to "solved"?

---

### Post by BobMarleyy on 2011-11-17
I also installed a different theme now, which seems to work better with notifications. Thanks for the advice.

To mark as solved, click Thread Tools (it is in red letters) and then you can select Mark as solved.

---

