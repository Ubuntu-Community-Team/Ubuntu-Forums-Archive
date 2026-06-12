---
title: "menu items after apt-get"
date: 2006-06-10
forum: Desktop Environments
---

### Post by exile on 2006-06-10
One thing that I have noticed about dapper that didn't seem to happen in the previous versions (for KDE at least) is that after installing two rather well known apps their entries aren't showing in the start menu. The apps are Scribus and Inkscape - in previous versions I'd just apt-get them and they'd be in the graphics and office sub menu's.

Can anyone explain why this is changed? Do I need to restart my session to see them (like gnome needed to be in the past)?

The commands were

sudo apt-get install scribus
sudo apt-get install inkscape


I can make the menu items myself, that isn't the issue it's more why did it change?

Other than this issue Dapper has exceeded everything else I've used. Great work and thanks!

---

### Post by aysiu on 2006-06-10
[http://www.monkeyblog.org/ubuntu/installing/#where_did_it_go](http://www.monkeyblog.org/ubuntu/installing/#where_did_it_go)

---

### Post by exile on 2006-06-11
Thanks, but that might work for Gnome but there was no luck for KDE. I restarted the session and the menu items were there.. it just seems to me to be a step back having to restart the session.

---

### Post by aysiu on 2006-06-11
You don't have to restart the session. Just press Alt-F2 and type ```
killall kicker
kicker
```

---

### Post by exile on 2007-03-21
Thanks, I suppose that wasn't really my question, I was wondering why the difference from past versions? I don't remember ever having a problem with menu items after installs on KDE, gnome yes, but KDE not that I'm aware of. I just felt that it seems to be an Edgy thing.

---

