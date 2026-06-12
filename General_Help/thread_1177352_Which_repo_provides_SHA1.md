---
title: "Which repo provides SHA1"
date: 2009-06-03
forum: General Help
---

### Post by satimis on 2009-06-03
Hi folks,


Ubuntu 8.04

I have libdigest-sha1-perl installed on repo.  But I can't find it running;
```

# which sha1/sha-1/SHA1/SHA-1

```

Please advise which package provides SHA1?  TIA

B.R.
satimis

---

### Post by Yellow Pasque on 2009-06-03
coreutils provides /usr/bin/sha1sum
Does that answer your question?

---

### Post by satimis on 2009-06-03
> **Temüjin said:**
> coreutils provides /usr/bin/sha1sum
Does that answer your question?
Hi Temüjin,

Thanks for your advice.

No, I need SHA1 command reading a text-password generating SHA1 hash to compare the encrypted passwords stored on MySQL database table.

B.R.
satimis

---

