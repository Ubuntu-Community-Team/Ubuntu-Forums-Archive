---
title: "Rsync options"
date: 2011-06-01
forum: Desktop Environments
---

### Post by asai on 2011-06-01
Hi,

I am looking for the correct use of Rsync options.

Here is my case:
I want to sync 2 folders, one on a desktop and the other on my server. My objective is to keep the desktop folder always updated with the content of the server folder.

If I get this working, I can do the same with the rest of my desktop and laptop users. When online they can run a script with rsync and update data.

Is it possible to get 2 way sync?

---

### Post by papibe on 2011-07-09
Did you solve your problem?

Using rsync over ssh would be the easiest way to do that. To get the lastest changes from the server:
```
$ rsync -av -e ssh server:/path/to/dir/ /local/path/
```
And this to push your changes to the server:
```
$ rsync -av -e ssh /local/path/ server:/path/to/dir/ 
```
Hope it helps.

---

### Post by SeijiSensei on 2011-07-09
If you want to make them exact copies, you'll probably want to use the --delete option as well.  I actually prefer not deleting files on the target to maintain an archive, but then I'm interesting in backing up one machine to another, not keeping them in sync.

---

### Post by asai on 2011-08-01
This solved my case. I use -delete because I need to have it synced, not backup. :)

---

