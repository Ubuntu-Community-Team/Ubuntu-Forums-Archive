---
title: "Gnome Do Firefox plugin not working at all"
date: 2009-03-01
forum: General Help
---

### Post by kpmoore on 2009-03-01
Just got my new Dell Mini 9 all setup with UNR and she's running great. Only problem I have is that the firefox plugin for Gnome Do will not index my firefox bookmarks. I searched around and no one else seems to have this problem. 

I'm running Firefox 3.0.6 and Gnome Do 0.8.0. Any suggestions?

---

### Post by kpmoore on 2009-03-01
Bumpin it.

I've even tried forcing firefox to export its bookmarks into the bookmarks.html files. I've tried to index bookmarks from the toolbar and the menu. No luck what-so-ever.

---

### Post by thtrgremlin on 2009-03-01
Can you please provide a link to either the deb package or the firefox plugin? It will be easier to track down the problem that way.

I thought you were talking about [this]("http://do.davebsd.com/"), but that isn't a plugin for firefox.

I found [this]("http://ubuntu-tutorials.com/2008/03/06/how-to-install-gnome-do-plugins/") page, which may help, but I still see nothing about firefox.

Let us know some more specifics.

---

### Post by kpmoore on 2009-03-01
Its not a plugin for firefox, its a plugin for Gnome Do. It, in theory, allows Gnome Do to index your Firefox bookmarks. 

I didn't use a deb for either Gnome Do or Firefox, just installed from the repositories.

---

### Post by vanadium on 2009-03-01
Just enabling the plugin in gnome-do preferences should do the trick. Perhaps, you need to allow some time before all of your bookmarks are effectively indexed.

---

### Post by kpmoore on 2009-03-01
The checkbox was checked many many bookmarks and restarts ago. It has had ample time to index them.

I'm wondering if it has anything to do with my having installed Ubuntu Netbook Remix. Can't image that it would, though.

---

### Post by thtrgremlin on 2009-03-01
I think I found a reference to the problem from v0.5, though it is said to be fixed.

[https://bugs.launchpad.net/do/+bug/229250]("https://bugs.launchpad.net/do/+bug/229250")

I found it through this page:

[https://answers.launchpad.net/do/+question/31135]("https://answers.launchpad.net/do/+question/31135")

Might be worth while to post your question there.. Seems like quite an active community. Since they are still at <v1.0, it is likely a bug you can report to help improve the software.

Sorry couldn't help further, bug good luck

---

### Post by kpmoore on 2009-03-01
Upon further investigation, I've found that it *is* indexing the bookmarks that come packaged with Firefox (i.e. Help and Tutorials, Ubuntu Help and Support, etc). But even placing my bookmarks in the same folders as these default bookmarks, Gnome Do will not index them.

---

### Post by pros on 2011-01-15
[https://bugs.launchpad.net/do/+bug/205824](https://bugs.launchpad.net/do/+bug/205824)
This works...

[https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll]("https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll")

The proposed patch, solves this problem in Lucid and Maverick.
Just replace the file in /usr/lib/gnome-do/plugins.

---

### Post by pros on 2011-01-15
[https://bugs.launchpad.net/do/+bug/205824](https://bugs.launchpad.net/do/+bug/205824)
This works...

[https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll]("https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll")

The proposed patch, solves this problem in Lucid and Maverick.
Just replace the file in /usr/lib/gnome-do/plugins.

---

### Post by pros on 2011-01-15
[https://bugs.launchpad.net/do/+bug/205824](https://bugs.launchpad.net/do/+bug/205824)
This works...

[https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll]("https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll")

The proposed patch, solves this problem in Lucid and Maverick.
Just replace the file in /usr/lib/gnome-do/plugins.

---

