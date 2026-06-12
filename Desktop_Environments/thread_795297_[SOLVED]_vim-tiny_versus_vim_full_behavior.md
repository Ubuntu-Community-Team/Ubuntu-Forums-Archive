---
title: "[SOLVED] vim-tiny versus vim full behavior"
date: 2008-05-15
forum: Desktop Environments
---

### Post by cmnorton on 2008-05-15
I was about to post a question here asking how to get Konsole to behave like xterm regarding how vim behaves when in insert mode and cursor keys are used. vim-full interprets the cursor keys, allowing you to move around during an insert. 

I searched around first, and came across a useful post:

[https://lists.ubuntu.com/archives/ubuntu-users/2008-January/133623.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-January/133623.html)

which talked about installing the full version of vim. I did, and the cursor keys work fine now.

Edit:
----------------------------------------------------------------------
Before installing the full version of vim, the cursor keys' escape values inserted into the insert stream, instead of being interpreted to move up, down, and so on.

---

