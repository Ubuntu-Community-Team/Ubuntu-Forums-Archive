---
title: "Evolution HTML linking problem"
date: 2008-06-06
forum: Desktop Environments
---

### Post by klunglejc on 2008-06-06
The other day I installed a lot of updates. Several of them was for Evolution. I now run Evolution 2.22.2. Ever since the updates were installed, when I click on a HTML link embedded within a Email it does not bring up Foxfire and make the connection automatically. I can right click and then copy the link and manually go to foxfire and paste the URL in and that works. But it will not do it automatically from within Evolution. Has any one else had this problem?

---

### Post by skiffler on 2008-07-06
I have exactly the same problem with 2.22.2 and Hardy. Any fixes for this? Very annoying.

---

### Post by the-linux-guy on 2008-07-06
> **skiffler said:**
> I have exactly the same problem with 2.22.2 and Hardy. Any fixes for this? Very annoying.

You need to set the URL handler for the GNOME 2.x desktop. Use gconf-editor, browse to desktop/gnome/url-handlers, look for http and https and set the path to your default browser in those keys...

---

### Post by kmori on 2008-08-05
I had the same problem.  It is caused from the fact that those paths in gconf aren't updated.  With 3.0.1 Firefox, they decided to install the new files under /usr/lib/firefox-3.0.1 instead of /usr/lib/firefox.
I just deleted the old files:

> sudo rm -rf /usr/lib/firefox

and then created a link from the new path to the old one:

> sudo ln -s /usr/lib/firefox-3.01 /usr/lib/firefox

and now the links work fine.

---

