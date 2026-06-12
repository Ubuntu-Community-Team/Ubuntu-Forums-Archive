---
title: "[SOLVED] cleansweep?"
date: 2008-03-15
forum: Desktop Environments
---

### Post by keratos on 2008-03-15
Is there a cleansweep type app for linux?

I have loads of packages on my system, having been playing for some weeks now, and would like to remove packages I dont use or have not been accessed for "some time". I cannot tell this from synaptic and was looking for something more intuitive than searching my synaptic, deleting what I think needs to be, then finding out its actually needed.

Even a hint at what might be "unsued" would be a start.

cheers

---

### Post by phidia on 2008-03-15
You could take a look at [this ]("http://ubuntuforums.org/showthread.php?t=410189&highlight=cleansweep") thread and the links within it.
Hope that helps.

---

### Post by keratos on 2008-03-15
I did, before,

but the link to [http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles) does not work for me.

What about for you? Could be my end!

---

### Post by kellemes on 2008-03-15
Couple of options..

This will 'guess' all packages which aren't required.
```
sudo deborphan --guess-all
```

You can combine the result so those packages get purged like so..
```
sudo dpkg --purge `deborphan --guess-all`
```

This also is used to clean up unused dependencies on your system.
```
sudo apt-get autoremove
```

---

### Post by keratos on 2008-03-15
many thanks

I used a combination of these and gtkorphan (found from other searches i performed)

all is well now. 

cheers

---

