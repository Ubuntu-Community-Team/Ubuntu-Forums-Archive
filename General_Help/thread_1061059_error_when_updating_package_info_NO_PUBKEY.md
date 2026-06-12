---
title: "error when updating package info: NO_PUBKEY"
date: 2009-02-05
forum: General Help
---

### Post by Mzwo on 2009-02-05
Hi,

When updating package information, I've been getting this message for quite a while now: 


```
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

Anything i can do, or somebody else's fault?

Haven't asked yet since as a former windows user I'm sort of used to ignoring error messages ... 

Thanks,

Mzwo

---

### Post by TheodoreBSlambs on 2009-02-06
had this problem today as well. i think this is the most recent post about it. just change the key he uses to yours.

[http://ubuntuforums.org/showthread.php?t=1058580](http://ubuntuforums.org/showthread.php?t=1058580)

---

### Post by plucky on 2009-02-06
> **Mzwo said:**
> Hi,

When updating package information, I've been getting this message for quite a while now: 


```
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

Anything i can do, or somebody else's fault?

Haven't asked yet since as a former windows user I'm sort of used to ignoring error messages ... 

Thanks,

Mzwo


You just need to add the Medibuntu key.

To do so open a terminal **Applications > Accessories > Terminal** and copy and paste this command ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Input login password,which will not echo and that should fix the problem.

See this [link](https://help.ubuntu.com/community/Medibuntu) for further information about Medibuntu repository.

Good Luck

---

### Post by Mzwo on 2009-02-06
thanks.
that did it.

Cheers,
Mzwo

---

