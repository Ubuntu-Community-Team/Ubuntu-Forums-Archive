---
title: "Compiz Crashes"
date: 2010-04-02
forum: Desktop Environments
---

### Post by zeug on 2010-04-02
I restarted my computer and, when I logged in, Compiz did not seem to have started as it normally does (meaning that the windows did not have title bars and I could not click on the windows to change between them).  I tried starting it with ```
compiz &
``` in a terminal that I evnetually got into and the windows got their title bars came back but none of my Compiz effects were enabled -- I think it just started Metacity.  Because of this, I decided to stop GNOME with ```
sudo /etc/init.d/gdm stop
``` and reinstall my graphics driver (NViDIA).  Restarted GNOME and everything seemed to work as per normal.  However, at some point it reverted back to Metacity instead.  I started Compiz again but it seems to still revert to Metacity randomly.

Any idea?

Thanks.

---

### Post by lidex on 2010-04-04
In "compizconfig-settings-manager -> window decoration -> command field" make sure you have this value:
```
/usr/bin/compiz-decorator
```

In "gconf editor>apps>metacity>general" make sure "compositing_manager is UNchecked.

Also make sure "compizconfig-backend-gconf" is installed and ccsm is configured to use it.

---

### Post by zeug on 2010-04-04
How do I make sure ccsm is configured to use "compizconfig-backend-gconf"?

It has not done this again since my last post.  Perhaps it was a one-time thing.

Thanks.

---

### Post by lidex on 2010-04-06
Open ccsm, click on "Preferences" in the left pane, bottom. Where it says "Backend" in the right pane, select "Gconf Configuration Backend"

---

### Post by zeug on 2010-04-06
All of that is as it should be already.

---

