---
title: "Bizarre Panel Problem"
date: 2011-07-14
forum: Desktop Environments
---

### Post by andyl123 on 2011-07-14
Hello,

Im having a rather bizarre problem with the gnome panel in ubuntu 11.04.

When i go to places and try to  home folder, desktop, etc with a mouse click, Nautilus does not open. Instead a really old looking program called textedit opens.

The only thing that doesnt cause textedit to open is clicking on computer.


I dont know how to solve this problem and would really appreciate some help

Andy

---

### Post by Krytarik on 2011-07-14
It seems like you inadvertently changed the default application to handle folders.

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it and how to prevent that in future:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Notice that the concerning option, and possible cause of your issue, isn't included in the "Open With -> Other Application" dialog anymore, at least in Nautilus.

Greetings.

---

### Post by andyl123 on 2011-07-15
Thanks thats fixed it

---

