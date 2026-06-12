---
title: "KDE trash can issue [Resolved]"
date: 2007-05-16
forum: Desktop Environments
---

### Post by Ateo on 2007-05-16
Anytime my KDE trash bin *not* empty, my desktop icon does not reflect being full. My icon set does have a full/empty trash icon.

Any ideas?

---

### Post by aysiu on 2007-05-16
Does this happen even if you rename /home/username/.kde to /home/username/.kde.old and then log out and log back in again?

---

### Post by Ateo on 2007-05-16
Yes, I have deleted .kde and .kderc (new install so I didn't lose anything) as part of my troubleshooting. This did not resolve the issue.

I've even deleted the trash bin and created a new 'Link to Location (URL)'.

---

### Post by aysiu on 2007-05-16
Well, I guess a cleaner test would be to create a new test user and see if that test user experiences the same problems. We're guessing (if it is a configuration file issue) that the config file is in ~/.kde or ~/.kderc, but it may be elsewhere. A new test user is the surest way to tell if it's a systemwide or user-specific problem.

---

### Post by Ptero-4 on 2007-05-16
> **Ateo said:**
> Yes, I have deleted .kde and .kderc (new install so I didn't lose anything) as part of my troubleshooting. This did not resolve the issue.

I've even deleted the trash bin and created a new 'Link to Location (URL)'.

I got the issue pinned (I think, long since I switched to gnome). Links AFAIK doesn´t have dynamic icon functionality. To have the trash bin on the desktop you have to enable it (It might be on the ¨Desktop¨ control panel).

---

### Post by Ateo on 2007-05-17
Hmm. Very queer. Creating a new user did not even create the trash can icon. From what I remember, my installation user didn't have a trash icon either which is what led me to create the icon....

I've checked and explored all the 'desktop' control panels. I didn't see anything that reference dynamic icons in any form...

---

### Post by aysiu on 2007-05-17
That's the problem. It's not an icon--it's an applet.

Right-click the panel and select to add an applet and then select the trash applet.

If you want the trash can on the desktop, [this tutorial](http://linuxfud.wordpress.com/2006/09/24/how-to-add-the-trash-can-to-your-kubuntu-desktop/) should help.

---

### Post by Ateo on 2007-05-17
> **aysiu said:**
> That's the problem. It's not an icon--it's an applet.

Right-click the panel and select to add an applet and then select the trash applet.

No. This isn't the problem my friend. I'm not talking about a trash can on my task bar.. =)

> **aysiu said:**
> If you want the trash can on the desktop, [this tutorial](http://linuxfud.wordpress.com/2006/09/24/how-to-add-the-trash-can-to-your-kubuntu-desktop/) should help.

*THIS* is what I was looking for. Thank you. It worked like a charm!!

---

### Post by aysiu on 2007-05-17
Whether it's on your task bar or your desktop, it still needs to be an applet, not just an icon. Glad the tutorial worked out for you.

---

### Post by Ateo on 2007-05-17
> **aysiu said:**
> Whether it's on your task bar or your desktop, it still needs to be an applet, not just an icon. Glad the tutorial worked out for you.

Right. But for the taskbar, I just 'add the applet' by right clicking on the taskbar.

Anyways, thanks again!

---

