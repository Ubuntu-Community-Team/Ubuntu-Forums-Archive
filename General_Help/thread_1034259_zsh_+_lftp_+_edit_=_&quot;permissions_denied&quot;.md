---
title: "zsh + lftp + edit = &quot;permissions denied&quot;"
date: 2009-01-08
forum: General Help
---

### Post by figgles on 2009-01-08
I can't figure out this problem.

Using lftp (works great in any other respect) I wish to edit a file while connected to a remote ftp server:

laptop% edit thisfile.php
zsh:1: permission denied: /home/sgt/.lftp/edit.tmp.18241

Of course I can download, edit and upload, but lftp on my Tiger/Mac OS works just fine.

Any ideas?

---

### Post by figgles on 2009-03-28
Turns out its a simple problem:

in zsh, add to .zshrc:

export EDITOR=vim

---

