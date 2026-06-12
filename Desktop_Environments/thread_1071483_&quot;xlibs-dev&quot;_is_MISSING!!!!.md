---
title: "&quot;xlibs-dev&quot; is MISSING!!!!"
date: 2009-02-16
forum: Desktop Environments
---

### Post by unix-vocab_trainwreck on 2009-02-16
if there are any moderators who are deeply involved in this, can anyone tell me where i can manually download the package:"xlibs-dev"? I am attempting to set up Openbox on my system (ubuntu hardy) and the last pre-requirement that was listed was this package. this is the error i get when i request for it by "sudo apt-get install xlibs-dev":
```
sudo apt-get install xlibs-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xlibs-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibs-dev has no installation candidate

```

i don't know where else to look at this point. And even worse, if i got it in raw form i wouldnt know what to do with it. Help!

and thanks to anyone who can:)

---

### Post by snova on 2009-02-16
Instead perhaps try **xorg-dev**- a metapackage that seems to fufill the same role.

In any case, why are you installing Openbox from source? You could simply install the **openbox** package...

---

### Post by unix-vocab_trainwreck on 2009-02-16
thanks snova, xorg-dev installed nicely. And to answer your question, i'm pretty new to all this, so i was just following the prereqs they gave on the opebox wiki. Besides that, I'm not exactly sure how to install and run things in the ubuntu gui that well yet.

  Also, is the xorg-dev package a shared component, is it only for openbox to use?

thanks yet again for you help

---

### Post by snova on 2009-02-16
> **unix-vocab_trainwreck said:**
> Also, is the xorg-dev package a shared component, is it only for openbox to use?

Yes. Any other software that needs X headers will find them.

And, on a side note, technically xorg-dev doesn't contain anything- it just depends on a bunch of other packages that contain the actual headers.

---

