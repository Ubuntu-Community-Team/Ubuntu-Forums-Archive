---
title: "Editing the gnome menu"
date: 2007-07-16
forum: Desktop Environments
---

### Post by nevernamed on 2007-07-16
I recently installed a development suite, foolishly thinking that maybe by some off chance it would run in gnome (there were little k's in front of all the programs in the suite). No luck. So I figured no big deal I'll just uninstall it. So I did. However, all the little icons that were created under Applications>Programming are still there and it clutters up my menu and annoys me.
The only remotely helpful thing I could find on the gnome website was this:
[http://www.gnome.org/start/2.0/menuediting.html#removeentries](http://www.gnome.org/start/2.0/menuediting.html#removeentries)
and I really don't understand what they're talking about. Does anybody know how to remove gnome menu entries?

Thanks in advance.

---

### Post by kvonb on 2007-07-16
Right click on the main menu bar and select "Edit menus" :)

---

### Post by N-t-F on 2007-09-03
Hi!

I'm sorry to hijack this thread, but my question is so close to the OP that I figured it would fit here just as well as in a new one.

I would like to remove a few elements from the "System -> Preferences" menu, not only for me but for every users of the computer (there are many of them). My first idea has been to run gconf-editor to set up a mandatory list of menu items, but I can't find them (a search for "scim" in gconf-editor brought 0 results, for instance).

Additionnally, Sbayon (the profiles tool) doesn't seem to manage menus.

Am I on the wrong track? :confused: Could someone give me a hint?

Thanks in advance.

N-t-F

---

### Post by N-t-F on 2007-09-04
Okay, I've finally found the answer:

> **Sam said:**
> Go into /usr/share/applications. This is where the launchers in the menus are stored. The one for the screensaver is screensaver-properties.desktop, there should be a copy of it if you see it twice.

Have a nice day.

---

