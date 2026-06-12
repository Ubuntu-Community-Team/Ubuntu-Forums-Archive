---
title: "groupwise 7"
date: 2006-01-05
forum: General Help
---

### Post by tekwarren on 2006-01-05
I've installed GW7 thanks to the info here in the forums but am having an issue getting it to run:

```
/opt/novell/groupwise/client/bin/groupwise
/opt/novell/groupwise/client/bin/groupwise: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

I looked up similar posts that said the make sure g++ (?) is installed and I ran the command to look for it and it said it was already up to date. 

Any ideas?

---

### Post by tekwarren on 2006-01-07
never mind my supervisor helped me figure this out. I had to install the libstdc++ library(?) and update java. Works like a champ now...I actually like it better than the windows version!

---

