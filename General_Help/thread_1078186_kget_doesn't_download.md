---
title: "kget doesn't download"
date: 2009-02-23
forum: General Help
---

### Post by AlmaTlust on 2009-02-23
I would like to use kget as download manager, but it doesn't actually download anything... The list ist displayed, but it says "delayed", no matter how often I restart the job. I tried deactivating different plugins, but to no avail..
Any help here? It's one of the reasons why I can't use konqueror for web browsing (there are others, but I won't talk about them here... ;-)

---

### Post by Benic on 2009-02-26
It seems to be a KDE 4 bug. Look [_here_]("https://bugzilla.novell.com/show_bug.cgi?id=396079") for more info.

There is a simple workaround that worked for me. Open Kget, go to Modules in configuration, and look for the Mutlithreaded http(s)/ftp(s) tab. Here, change the thread number from 4 to 1. Restart Kget and that's it.

---

