---
title: "Vim tilde files!"
date: 2005-03-04
forum: Desktop Environments
---

### Post by HungSquirrel on 2005-03-04
Does anyone know of a way to keep vim from leaving tilde files around after you edit a file?

For those who don't know what I'm talking about, if you open a file such as *foo.txt* in vim, once you exit and do an *ls*, you'll see not only *foo.txt* but *foo.txt~* as well.  This is annoying to me and I've always wondered how to get it to not do that.

---

### Post by p!=f on 2005-03-04
Perhaps these link might help you
[https://mail.fukt.bth.se/pipermail/crux/2003-October/001237.html](https://mail.fukt.bth.se/pipermail/crux/2003-October/001237.html)
[http://www.vim.org/tips/tip.php?tip_id=20](http://www.vim.org/tips/tip.php?tip_id=20)

---

### Post by HungSquirrel on 2005-03-04
Thank you!  I made a directory ~/.vimswaps and put...
```
set backupdir=~/.vimswaps,/tmp
```
...in my ~/.vimrc and things are nice and clean now.

---

### Post by p!=f on 2005-03-05
How about make this default, devs? :)

---

### Post by HungSquirrel on 2005-03-05
While the devs are at it, they should copy /usr/share/vim/vim63/vimrc_example.vim to /etc/skel/.vimrc .  If I recall correctly, I had to do this manually to get vim to behave as I am used to it behaving.  I could be mistaken though.  I try so many distros, it's hard to keep track!

---

