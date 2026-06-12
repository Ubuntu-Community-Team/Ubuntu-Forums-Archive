---
title: "Could not find package"
date: 2009-06-25
forum: General Help
---

### Post by burcyril10 on 2009-06-25
I just installed 9.04 Server and for some reason I can't use apt-get much.

I was getting "Could not find package" on dhcp3-server which I knew to be wrong, but then found the command to get it from cdrom, so that solved that - problem is now I need a package I know to be in universe but it keeps saying "Could not find package".
Yes i do have a connection to the internet (i can wget the index.html)
So therefore yes I have the correct url in sources.list (why wouldn't I, fresh install...)

Hope that all makes sence

Thanks in advance
Cyril

---

### Post by mk1w86 on 2009-06-25
Do you defiantly have the universe repo enabled in sources.list and then run 

```
sudo apt-get update
```

to update your package lists?

Also are you using the exact name of the package in the install command?

---

### Post by burcyril10 on 2009-06-25
Legend! Problem solved, but if you're curious lol I needed ipfm :).

---

