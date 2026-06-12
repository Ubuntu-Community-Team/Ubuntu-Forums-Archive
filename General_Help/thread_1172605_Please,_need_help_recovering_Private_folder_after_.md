---
title: "Please, need help recovering Private folder after reinstalling Jaunty"
date: 2009-05-28
forum: General Help
---

### Post by Anony_C on 2009-05-28
After having trouble reverting some changes I made to Xorg, I decided to reinstall 9.04.
The problem I discovered afterward was that I forget to write down my passphrase, or backup the files laid therein my Private folder.

I still have the ".Private" and ".ecryptfs" folder backed-up but have yet to discover a way to decrypt my original Private folder.

I've tried reinstalling "ecryptfs-utils"; overwriting .ecryptfswith my original (with the wrapped-passphrase); then "$ ecryptfs-unwrap-passphrase" and this was the result:

```
$ ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase "login passphrase"
Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs
```

Help please. :(

---

