---
title: "SVN won't let me commit any more..."
date: 2006-10-01
forum: Desktop Environments
---

### Post by kerinin on 2006-10-01
I've been using subversion for repository control on a few projects i'm working on, and everything was working fine.  i could import, checkout, commit, etc.

then a day or two ago i started getting the following error when i tried to commit from the computer where the svn server is located:

```
kerinin@simon:~/Projects/web/organizer$ svn commit
svn: Commit failed (details follow):
svn: Can't create directory '/home/svn/organizer/db/transactions/18-1.txn': Permission denied
svn: Your commit message was left in a temporary file:
svn:    '/home/kerinin/Projects/web/organizer/svn-commit.tmp'

```

the working copy that i was trying to commit was checked out with 'svn file:///home/svn/organizer'.  when i run 'sudo svn commit' it works fine. also, when i commit via https from other computers i don't have any problems. 

I chowned the entire /home/svn directory and subversion:www-data, and chmodded it rwx for user and group, and then added the www-data to my user's groups.  

What do i need to do to be able to commit without sudo?

Thanks

---

