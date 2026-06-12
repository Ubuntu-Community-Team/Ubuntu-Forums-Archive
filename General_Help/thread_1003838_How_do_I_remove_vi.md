---
title: "How do I remove vi?"
date: 2008-12-06
forum: General Help
---

### Post by hardysummer on 2008-12-06
It comes by default, and I do not want it.  How do I remove it?  It is there obviously, but apt says that it is not.

Instructions in CLI, please.

---

### Post by lovelyvik293 on 2008-12-06
Hai it's not the vi/vim full version it's vim-tiny the compact version of vi/vim.
And it's part of ubuntu-minimal.

---

### Post by kerry_s on 2008-12-06
vi = vim
**sudo apt-get remove --purge vim-***

---

### Post by andrew.46 on 2008-12-07
Hi,

Perhaps instead of the commands given already, which have the unfortunate effect of ridding your computer of a great piece of software, you could try the following:

```
$ sudo apt-get install vim-full
$ vimtutor
```

and come to grips with a great text editor :-).

  Andrew

---

### Post by russo.mic on 2008-12-08
Agreeing with above, and also looking to point out it's not as if your saving a tremendous amount of harddisk space.

Russo

---

### Post by kerry_s on 2008-12-08
not every one wants to learn or cares to learn vi/vim.
nano also comes on most distro's and is far easier for new comers to wrap there head around especially when they want to be in and out of cli as fast as possible.

---

### Post by theozzlives on 2008-12-08
removing vi from Linux is like removing edlin from DOS

---

