---
title: "&quot;klauncher said: Unknown protocol 'system'.&quot;"
date: 2006-02-17
forum: Desktop Environments
---

### Post by Fjodor on 2006-02-17
Hi.

Above message, and the equivalent for trash is shown on KDE startup. Original install is ubuntu plain, with a subsequent apt-get install kubuntu-desktop.

How to remedy?

Best regards,

Fjodor

---

### Post by tico on 2007-08-26
I've Xubuntu and installed Krusader. I've set it up to trash files (and not delete files: settings> configure Krusader> General> General). I used to work fine, but now I'm getting the following error message:

could not start process. Unable to create io-slave: Klauncher said: Unknown protocol "trash".

How could I solve this?

Thanks.

---

### Post by kellemes on 2007-08-26
Krusader is a KDE-app so I can imagine it will try to use the KDE trash , which is not available in XFCE, maybe this is the issue?
Isn't there a way to disable this "delete to trash" in Krusader?

---

### Post by tico on 2007-08-26
> **kellemes said:**
> Isn't there a way to disable this "delete to trash" in Krusader?

Yes, there is, but I'd like to use trash, not to delete directly.

---

### Post by LianaXu on 2007-09-02
> **kellemes said:**
> Krusader is a KDE-app so I can imagine it will try to use the KDE trash , which is not available in XFCE, maybe this is the issue?
I guess that really is the issue. 
But nevermind. Write your own useraction. When pressing "del" for example call the move command and move the selected file(s) to your XFCE/Gnome Trash directory. I use Gnome and it's working for me (at least for the dell button, not yet for the menu). Hope it's working for you too.

---

