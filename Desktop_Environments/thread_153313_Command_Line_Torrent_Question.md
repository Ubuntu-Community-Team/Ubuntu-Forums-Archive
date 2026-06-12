---
title: "Command Line Torrent Question"
date: 2006-03-31
forum: Desktop Environments
---

### Post by kitchens on 2006-03-31
I'm using btdownloadheadless via ssh into my home machine. Its working ok but there is one thing I'd like it to do that either I don't know how to to, or its isn't possible. I'd like to be able to tell the torrent to run in the background until it reaches a certain share ratio. That way I could close my ssh session and leave the torrent running. Got any pointers? -Thanks in advance.

---

### Post by trent dillman on 2006-03-31
I don't know about ratio, but why not use nohup and leave it run until you manually kill it?

---

### Post by musther on 2008-06-07
Look for information on the command line program 'screen'.

It's very useful, basically, you SSH in, start screen, start your torrent download, (or whatever else), then close your SSH session.  When you reconnect, you open screen (with -r to tell it to reconnect to the old screen session) and you're back where you left off!

---

