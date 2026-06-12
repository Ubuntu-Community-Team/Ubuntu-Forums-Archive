---
title: "Update Manager won't update Compiz"
date: 2006-10-07
forum: Desktop Environments
---

### Post by jrohde on 2006-10-07
Hi,

For some reason, the package "compiz" keeps popping up in the update manager with a message saying that it can't be updated. It doesn't say why.

Any suggestions?

Jakob

---

### Post by lemonsCC on 2006-10-07
In terminal run:
```
sudo apt-get update
sudo apt-get upgrade
```

post any errors here

---

### Post by jrohde on 2006-10-07
Hi lemonsCC

Thanks, but that doesn't do the trick. It's the same thing - "compiz" can't be updated.

Other ideas?

Jakob

---

### Post by bulldog on 2006-10-07
If you use the quinnstorm repo's you won't get any update of compiz anymore.

They changed a lot read about it here.

[http://forum.beryl-project.org/](http://forum.beryl-project.org/)

You have to change to Beryl and emerald.

The support for Compiz,cgwd and csm is stopped and no further devellopement is done.
The packages are out of their repo's for a while now.

---

### Post by jrohde on 2006-10-07
Hi bulldog,

Thanks. Problem gone!

Jakob

---

