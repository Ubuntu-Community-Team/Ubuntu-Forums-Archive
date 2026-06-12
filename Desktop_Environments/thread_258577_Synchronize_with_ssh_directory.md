---
title: "Synchronize with ssh directory?"
date: 2006-09-16
forum: Desktop Environments
---

### Post by oocce on 2006-09-16
I'm using [COLOR="Red"]rsync[/COLOR] to synchronize with remote directory, but with no good results.
I have read rsync man-page but with my english skills its not getting me anywhere! I have managed to transform files but I want transfer files both way.

I have "School"-directory at my home computer and "School"-direcory at my schools ssh-server. How I do that? It is possible to run with one command or must I do two commands? Only options are that it should sync files, folders, timestamps and new files. Removing is not necessary.

With Unison I get error: "Fatal error. Lost connection with the server".

Thanks for all helpers!

---

### Post by justynbutler on 2006-10-28
"[Unison] uses the rsync algorithm to keep network traffic down and should be tunneled through SSH over untrusted networks. No extra work is needed-simply specify ssh:// when adding a directory location."

From this webpage:
[http://www.linuxjournal.com/article/7712](http://www.linuxjournal.com/article/7712)

Presumably this is what you're doing when you get the error?

---

