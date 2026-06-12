---
title: "Firefox bookmarks don't update until restart"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Beanalby on 2007-04-22
I've been using Ubuntu & Firefox for a while, just did a fresh install of Festiy Fawn and I'm having problems with bookmarks in firefox.

When I make any changes to my bookmarks or bookmarks toolbar folder, the changes aren't reflected until I restart firefox.

For example, if I bookmark the current page, it doesn't show up in bookmarks.  If I restart firefox, it's there.  If I right-click on a bookmark and say "Delete...", it isn't removed from the Bookmarks menu.  If I right-click again on it, it only has the options "Open", "Open in Window", and "Open in New Tab", as opposed to the full context menu that appears on most links.  Once again, restarting firefox properly removes the entry.

The same symptoms appear in the "Organize bookmarks" window, except closing and re-opening Organize Bookmarks is enough to get it to realize the changes.  The Bookmarks Toolbar Folder won't show updates until reboot though.

I've been using Firefox since the pre-1.0 days, but I've never seen behavior like this.  Everything else in firefox (and all other programs) seem fine.  Any ideas?

---

### Post by orb9220 on 2007-04-22
about:plugins in address bar and post version of java listed there
also check version of firefox and post.

---

### Post by Beanalby on 2007-04-22
> **orb9220 said:**
> about:plugins in address bar and post version of java listed there
also check version of firefox and post.

No java plugin  listed
[http://home.beanalby.net:88/plugins.html](http://home.beanalby.net:88/plugins.html)

java 1.4.2 appears to be installed on the system.

```
ninji@littlebean:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

```

Firefox version is 2.0.0.3 according to help->about

All this is Feisty Fawn default.

---

### Post by Beanalby on 2007-04-22
Actually I just tested again and it seems to be working now.  I've done a full system reboot since then so that must've cleared it up.  I had done some bookmark imports so maybe that confused it.  Thanks!

---

