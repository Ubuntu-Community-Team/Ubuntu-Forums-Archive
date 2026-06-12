---
title: "VBox wants to compile kernal module."
date: 2009-01-29
forum: General Help
---

### Post by Universal344 on 2009-01-29
I recently tried to start openSUSE11.1 from Virtual Box 2.1 and got an error message about a kernal problem I believe.  It told me I should reinstall virtual box.  First, though, I remove virtualbox-ose-source suspecting it was the cause of the problem.  At any rate during install it asked if I wanted to compile a new kernal module because it could not find a compatible one.  Should I let it go ahead and compile a new one?

---

### Post by cicatrix1 on 2009-01-29
> **Universal344 said:**
> I recently tried to start openSUSE11.1 from Virtual Box 2.1 and got an error message about a kernal problem I believe.  It told me I should reinstall virtual box.  First, though, I remove virtualbox-ose-source suspecting it was the cause of the problem.  At any rate during install it asked if I wanted to compile a new kernal module because it could not find a compatible one.  Should I let it go ahead and compile a new one?

Yes.

Any time you update your kernel, vbox will need an updated module.  You did not have to uninstall.

If you run into this again in the future (which you will when a new kernel comes out):

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Universal344 on 2009-01-29
OK, thank you very much.  I hope this works.

---

