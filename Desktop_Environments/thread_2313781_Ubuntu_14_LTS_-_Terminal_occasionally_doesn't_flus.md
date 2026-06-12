---
title: "Ubuntu 14 LTS - Terminal occasionally doesn't flush most recent lines"
date: 2016-02-15
forum: Desktop Environments
---

### Post by newnotice on 2016-02-15
This is a weird problem I've been having for a while now, occasionally I will type something in Ubuntu like a command to git and I don't see all the lines of output immediately. In other words it looks like the process has hanged but that's never the case. Instead what has happened is the output isn't appearing in the terminal, like it isn't flushed. git is just one example it happens randomly with different commands.

For example right now I'm bisecting in git, and I typed that I bisect was bad so I see
$ git bisect bad
Bisecting: 13 revisions left to test after this (roughly 4 steps)

But it doesn't show the actual text that comes after that even though the command is already done, it just appears to hang. So I can hit enter and it will show me whatever wasn't flushed. That should be unnecessary though. Any ideas?

---

