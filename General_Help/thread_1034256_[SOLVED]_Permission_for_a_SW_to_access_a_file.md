---
title: "[SOLVED] Permission for a SW to access a file"
date: 2009-01-08
forum: General Help
---

### Post by Gyula on 2009-01-08
Hello everybody, I had the following question.

I installed a software in Ubuntu and now I try to upgrade its license. During this process, the software wants access to the appropriate license file. At this point I get the message that says "permission denied".

The question is quite simple (I am absolute beginner): how can I grant the required permission?

Many thanks in advance!

Gyula

---

### Post by jgoguen on 2009-01-08
The licence file was likely installed owned by root (or at least, not owned by you).  You could run this command, replacing "username" with your username, to make the licence file owned by you:
```
sudo chown username:username /path/to/licence/file
```
That will make only the licence file owned by you, and hopefully that's enough to let the program proceed.

---

### Post by Gyula on 2009-01-08
Many thanks, problem solved. You saved my day.

Is it such a operation for a whole directory as well?

---

### Post by jgoguen on 2009-01-08
It's very similar for an entire directory.  If you wanted to make the entire directory and everything under it owned by you, then you would use this command:
```
sudo chown -R username:username /path/to/directory/
```The **-R** means "recursive", which means it'll apply the change to the directory and everything it finds inside it (and inside sub-directories, and sub-directories of sub-directories...).  Without that option, chown would only change the directory, but nothing in it, meaning you could create new files but not edit existing ones.  In general though, you shouldn't go changing permissions on entire directory structures without a good reason.

Also, since your problem is solved, please mark the thread as solved.  This will let other people browsing the forums know that you got an answer to your question.  To mark threads solved, click the **Thread Tools** link.  It's just above and to the right of your first post.  This will make a menu appear.  Choose the option from the menu to mark the thread solved.

Thanks :)

EDIT: I just noticed that this is your first set of posts.  Welcome to the Ubuntu Forums, and to Ubuntu! :)

---

### Post by Gyula on 2009-01-08
Many thanks for the warm welcome :)

---

