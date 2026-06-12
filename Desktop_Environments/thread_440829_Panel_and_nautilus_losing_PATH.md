---
title: "Panel and nautilus losing PATH"
date: 2007-05-12
forum: Desktop Environments
---

### Post by dogamnit on 2007-05-12
Been using Feisty awhile and after logging back in (after several days logged on) the panel and nautilus lose my PATH which has ~/bin set. I put it in .gnomerc and .profile. These get executed and show PATH (via echo $PATH >$HOME/path) with ~/bin. Not sure what I may have inadvertently changed.

cat .profile
if [ -d ~/bin ] ; then
    export PATH=~/bin:${PATH}
    echo "$PATH" > ~/path
fi

puzzled

---

