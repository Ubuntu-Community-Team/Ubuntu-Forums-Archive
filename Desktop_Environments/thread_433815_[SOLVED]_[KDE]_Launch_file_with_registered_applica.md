---
title: "[SOLVED] [KDE] Launch file with registered application"
date: 2007-05-05
forum: Desktop Environments
---

### Post by Cygnus on 2007-05-05
I am programming an application for KDE which works fine, but I have browsed around a lot to try to find how to open a file with its registered application in KDE. That is, what should I use in the KDE api to achieve this ? I think I have gone blind or something, because it should be a really common operation.

---

### Post by k7k0 on 2007-05-05
Hello,
You can use **kfmclient**  (KDE tool for opening URLs from the command line)

Its like the windows's start command (or gnome gnome-open). For example:
```

kfmclient exec $file

```

---

### Post by Cygnus on 2007-05-05
Yes thank you very much that works fine :)

Although I have a feeling that there is some nicer way to do it rather than calling kfmclient using system()., but this will have to do for now.

---

