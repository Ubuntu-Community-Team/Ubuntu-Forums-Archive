---
title: "Gnus on Emacs no longer works"
date: 2006-06-02
forum: Desktop Environments
---

### Post by pchachte on 2006-06-02
Hi,

I just installed dapper and everything seems to work fine, except that gnus is no longer working. I get the following errors.

movemail: /usr/lib/emacs/21.4/i486-linux-gnu/movemail: error while loading shared libraries: liblockfile.so.1: cannot open shared object file: No such file or directory (127 return).  Continue? (yes or no) 

Any one have any ideas where I might look to solve this problem?

Thanks

---

### Post by pchachte on 2006-06-04
I fixed it, though I think there is a bug in gnus packaging.

First I had to download a package:

sudo apt-get install liblockfile1

Then I had to add a gnus directory that I had never needed before:

mkdir ~/gnus

Now it's working fine. ;-}

Thanks to anyone who thought about this!

---

### Post by pchachte on 2006-06-06
Here's the relevant bug report for those interested. My previous suggestion is correct: install liblockfile1

[https://launchpad.net/distros/ubuntu/+source/emacs21/+bug/48656]("https://launchpad.net/distros/ubuntu/+source/emacs21/+bug/48656")

---

