---
title: "An image file instead open any folder from &quot;Places&quot;"
date: 2011-03-21
forum: Desktop Environments
---

### Post by xumuk37 on 2011-03-21
Hi folks! Since this morning when I try to open any place from "Places" xD, I get an image from any folder inside my $HOME...

[IMG]http://img694.imageshack.us/img694/4168/screenshotce.png[/IMG]

 Some idea how could I fix it?

[RIGHT]Thanks in advance![/RIGHT]

---

### Post by Krytarik on 2011-03-21
Try this: Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

