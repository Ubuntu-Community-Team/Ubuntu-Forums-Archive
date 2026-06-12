---
title: "Deleting Home.backup Help"
date: 2009-03-02
forum: General Help
---

### Post by BigDaveyJ on 2009-03-02
So I decided to use this command to make my wubi installation bigger.```
sh wubi-add-virtual-disk /home 15000
```

But I forgot to change 15000 to 80000. And now I have been trying to delete the home.backup directory it made. But every time I try I get permissions denied. What is the command that gives me full permissions in a file browser?

Never Mind! Its Nautilus.

---

### Post by InspiredIndividual on 2009-03-04
I'm not sure whether you edit means the problem is already solved for you... I'll answer anyway, if only for others with a similar problem that may stumble upon this thread. If you want to run a graphical application with root permission, it's preferable to use gksudo instead of sudo. See the following for an explanation why: 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

So to run Nautilus with sudo permission, you'd issue the following command in a terminal:

```
 gksudo nautilus 
```

This enables you to change files where you normally wouldn't be permitted to, etc. Be careful, though! It's bad practice to use sudo permissions when not necessary, for quite obvious reasons.

---

