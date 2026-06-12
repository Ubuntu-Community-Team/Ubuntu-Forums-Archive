---
title: "Reset KDE to default settings"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Marshall2day on 2006-02-22
Hi, I've started out with ubuntu and decided to give KDE a try. I kind of screwed up my panels and stuff and I was wondering if there is a way to get me a default kde without having to reinstall my complete system. I tried to completely remove kde (with config files), but when I reinstall it my panels are the same as before which is f*cked up.

---

### Post by kwaanens on 2006-02-22
Remove the .kde dirs in your home. Log in again. In gnome, there's .gnome, .gnome2, .gnome-private and so on, so there may be several dirs you need to delete.

- Ketil

---

### Post by Marshall2day on 2006-02-22
Thanks, I will try that when I get home.

---

### Post by Vadi on 2007-10-31
Thank you. I had a similar case, and this worked for me.

---

### Post by T*&amp;1p87)v# on 2007-11-06
wait guys,i think under .kde there is the apps fodler where for example kmail saves your
mails and attachments, i guess it is not the best idea to remove the whole .kde or???

---

### Post by GeneralZod on 2007-11-06
> **ayarov said:**
> wait guys,i think under .kde there is the apps fodler where for example kmail saves your
mails and attachments, i guess it is not the best idea to remove the whole .kde or???

That's correct - you should never delete ~/.kde as there can be lots of important data stored there.

---

### Post by samwyse on 2007-11-06
My mail is in ~/Mail not in ~/.kde. However ~/.kde has some personal config stuff that one might want to keep (for example Amarok, Kmail config and Konqueror bookmarks). I just fixed an "unsolvable" problem by backuping the dir then removing the dir. After that I copied some of my configs back (mostly in ./kde/share/apps and ./kde/share/config) which I didn't want to reconfigure.

---

