---
title: "A *real* answer please: Removing &quot;Network&quot; from 'Places' menu"
date: 2007-08-14
forum: Desktop Environments
---

### Post by lns on 2007-08-14
There are way too many unanswered threads about this topic.

I am building 7 LTSP servers using Gnome as the main desktop environment in elementary/middle school settings. I need to remove potentially hazardous items from the "Places" menu, such as "Connect to Server", and "Network". What is the easiest way of doing this?

I know this isn't a "real" security fix by any means - but as the saying goes, "out of sight, out of mind." My customer wants these items removed...so I must do it. =)

Thanks for any help!

---

### Post by astoltz on 2007-08-14
Don't know what you mean by 'real' and I'd bet this doesn't qualify, but...

Why don't you just remove the whole menu bar from the panel and build one that has just what you need / want?

---

### Post by bmartin on 2007-08-14
> **lns said:**
> There are way too many unanswered threads about this topic.

I am building 7 LTSP servers using Gnome as the main desktop environment in elementary/middle school settings. I need to remove potentially hazardous items from the "Places" menu, such as "Connect to Server", and "Network". What is the easiest way of doing this?

I know this isn't a "real" security fix by any means - but as the saying goes, "out of sight, out of mind." My customer wants these items removed...so I must do it. =)

Thanks for any help!
I used to use Gnome. I fired up gnome-panel within Fluxbox to see if I could help you at all. I looked all over Google and searched through gconf-editor. I've looked in the config files for update-menus. It seems that you can't remove things from the Places menu. Consider Xfce or KDE. I don't think Gnome fits the bill.

---

### Post by mannheim on 2007-08-15
These entries are hard coded. But you can remove them by deleting or renaming the items to which they refer. So, to remove the "Connect to server ..." menu item, do:

```
sudo mv /usr/bin/nautilus-connect-server /usr/bin/nautilus-connect-server.hidden
```

and to disable the "Network" item, do:

```
sudo mv /usr/share/applications/network-scheme.desktop /usr/share/applications/network-scheme.desktop.hidden
```

(Do a "killall gnome-panel" after this to reload the panel and see the changes.) Of course, the first of these in particular may have other unwanted side-effects! And I'm sure this is a **really bad **thing to do (or a bad way to do it) from many points of view.

---

### Post by aysiu on 2007-08-15
Try Pessulus. It's in the repositories.

---

