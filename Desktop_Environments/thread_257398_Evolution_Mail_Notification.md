---
title: "Evolution Mail Notification"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Zill on 2006-09-14
Any ideas about how to configure Mail Notification 2.0 to work with standard POP3 Evolution 2.6.1.  "Autodetect" doesn't seem to find the Evolution Inbox and even typing the path in doesn't seem to help.
I have also installed evolution-dev as I read that that was needed to get the Evolution plug-in to work but this has made no difference :-(
Many thanks.

---

### Post by srf21c on 2006-11-09
got it working on a fresh install of Ubuntu Edgy 6.10.  

1) sudo aptitude install mail-notification-evolution

2) run mail-notification from terminal or "run application" dialog box.

3) Click the "add" button on the general tab, and selection "Evolution" as the mailbox type. Then pick a folder (usually Inbox) from the folder list below

4) You might want to click on the mail summary pop-up tab, and enable that as well.

Project page:
[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

Evolution mailing list archives:
[http://www.mail-archive.com/evolution-list@gnome.org/](http://www.mail-archive.com/evolution-list@gnome.org/)

---

### Post by Aranel on 2006-11-09
> **srf21c said:**
> got it working on a fresh install of Ubuntu Edgy 6.10.  

1) sudo aptitude install mail-notification-evolution

2) run mail-notification from terminal or "run application" dialog box.

3) Click the "add" button on the general tab, and selection "Evolution" as the mailbox type. Then pick a folder (usually Inbox) from the folder list below

4) You might want to click on the mail summary pop-up tab, and enable that as well.

Project page:
[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

Evolution mailing list archives:
[http://www.mail-archive.com/evolution-list@gnome.org/](http://www.mail-archive.com/evolution-list@gnome.org/)

That, however, requires Evolution to be running all the time. That's pretty annoying, but I've found a solution called Devil's Pie (sudo aptitude install devilspie), which automatically runs Evolution in a second workspace.

To make Evolution behave like this, create a folder called ~/.devilspie/, create a file called "evolution.ds" in that folder, and open it in your favorite text editor. Enter the following into it:

```
(if (contains (window_name) "Evolution") (begin maximize (set_workspace 2)))
```

Save, open a terminal, and type "cd .devilspie/" followed by "chmod a+x evolution.ds" to make it executable. Finally, go to System -> Preferences -> Sessions on the menu and click the "Startup Programs" tab; once there, add both "evolution" and "devilspie" to the list. Evolution should now pop up in workspace 2 every time you login; logout and back in again to test it.

---

### Post by srf21c on 2006-11-09
Righteous!  I will give that a try.  Thanks for posting the tip.

---

### Post by Zill on 2006-11-10
Thanks for the info srf21c.  I have found out that uptimebox has kindly produced a deb version with Evolution support.  Seems to work fine with Dapper :-)
[http://ubuntuforums.org/showthread.php?t=209361](http://ubuntuforums.org/showthread.php?t=209361)
[http://rolevikov.net/debian/mail-notification_3.0.uptimebox.2_i386.deb](http://rolevikov.net/debian/mail-notification_3.0.uptimebox.2_i386.deb)

---

### Post by srf21c on 2006-11-10
No prob, but I'm a little confused now.  There's already a package in the Edgy repos for "mail-notification-evolution" plugin, which is also version 3.0.  So what does one gain by using uptimebox's version?

Also, I have setup Devilspie according to the instructions above, it doesn't appear to offer any "new message" icons in the gnome notification area. Nor does it seem to offer any information mail message popups like mail-notification does.   Evolution did launch at login in the second workspace, but so far I am unimpressed with the functionality of devilspie vs mail notification.  Am I missing something?

---

### Post by Completenutter2 on 2006-11-18
I would guess you should run both, and all devils pie does, is move evolution to another workspace, so its hidden.

---

