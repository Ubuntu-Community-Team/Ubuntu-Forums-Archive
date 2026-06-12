---
title: "How do I limit ram usage?"
date: 2009-02-01
forum: General Help
---

### Post by Survivalism on 2009-02-01
Been searching for a week or so with no luck.

I need to know how to create a user acct that only uses 4g (out of 8g) of ram.  I have heard of it, but don't recall where.  Some sort of code you put in somewhere that locks the max usage.

---

### Post by lensman3 on 2009-02-01
Look at "bash"es ulimit command.  I think you can globally set ulimit in /etc/bashrc so that all child processes are limited by it.  There are a lot of options and I'm not sure which one(s) to set.

A possible problem I see, is when a user first log in and you want the process size to be limited. I'm not sure how ulimit get passed to all the sub and child processes.  That is, does the log in ulimit get passed to all subsequent processes.   Also I don't see a way around the user just resetting the ulimit in their own processes.

You might download the bash source code and see which system calls bash uses to limit the processes.

Hope this helps.

---

### Post by Survivalism on 2009-02-01
I wish it did.  I am not very familiar with Linux, and am still learning a lot of things.  I have no clue what bash is or how to manipulate it (I'm *so happy* that corporate giants have convinced me that I don't need to know anything).

The "ulimit" thing sounds familiar, though.  Something like "-ulimit 4000000" being added in somewhere.

If anyone has an answer to this, I have no problem getting my hands dirty as long as someone is sure of what I need to do.

---

