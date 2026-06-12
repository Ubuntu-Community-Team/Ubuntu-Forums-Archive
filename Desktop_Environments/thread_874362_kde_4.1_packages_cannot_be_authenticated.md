---
title: "kde 4.1 packages cannot be authenticated"
date: 2008-07-29
forum: Desktop Environments
---

### Post by someguy91 on 2008-07-29
I typed in 

sudo apt-get dist-upgrade

and then it tells me that a huge list of stuff cannot be authenticated? I already have kde 4.0 installed and before this, just added the launchpad sources link... did I do something wrong out of order?

Thanks very much in advance...

p.s. or is this supposed to happen?

---

### Post by warp99 on 2008-07-29
> **someguy91 said:**
> I typed in 

sudo apt-get dist-upgrade

and then it tells me that a huge list of stuff cannot be authenticated? I already have kde 4.0 installed and before this, just added the launchpad sources link... did I do something wrong out of order?

Thanks very much in advance...

p.s. or is this supposed to happen?

That just means their is no signing key for the packages. You can still install them without any problems.

---

### Post by kuja on 2008-07-29
It's supposed to happen, and it can safely be ignored. It just means that you don't have the key that it was signed with to verify that it is "not a fraud" so to speak, you shouldn't have anything to worry about.

---

