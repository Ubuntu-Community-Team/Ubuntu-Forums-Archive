---
title: "[Ubuntu-Gnome] Ubuntu dock not working after a crash"
date: 2020-04-01
forum: Desktop Environments
---

### Post by sandman42 on 2020-04-01
Hi all,

I have a 18.04 Ubuntu in a VM under VMWare Workstation Pro 15.5
After a crash of the host PC, and a fsck, Ubuntu dock no longer works correctly: if I try to add some app to favorites, such as terminal, by launching the app, right click on its icon in dock, Add to favorites, I get the message that the app has been added, but it isn't true because if I exit I don't find it on the dock anymore, and if I do a

```
gsettings get org.gnome.shell favorite-apps
```

I don't see it. The other strange thing is that I get this answer:

```
['ubiquity.desktop', 'firefox.desktop', 'thunderbird.desktop', 'org.gnome.Nautilus.desktop', 'rhythmbox.desktop', 'libreoffice-writer.desktop', 'org.gnome.Software.desktop', 'yelp.desktop']
```

But thunderbird, rhythmbox, writer and yelp are not shown on dock.

How con I fix it?

Thanks

---

