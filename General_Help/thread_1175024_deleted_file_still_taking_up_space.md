---
title: "deleted file still taking up space"
date: 2009-05-31
forum: General Help
---

### Post by Bunny Boy on 2009-05-31
Running Ubuntu 8.04 on a Dell laptop, I had a large file, around 2.6 GB, that I wanted to delete.  I selected it and sent it to trash, but when I go to empty trash, it's not there.  Also, before the delete there was only 1.6 GB free space on my hdd, and that hasn't changed. 

This file was in the root diretory, and I used sudo su to get there and delete (trash) it.  

Any idea what to do?

---

### Post by michy99 on 2009-05-31
It is in root's trash. ```
sudo rm -r /root/.local/share/Trash
```
Be careful! sudo rm is very powerful!

---

### Post by Bunny Boy on 2009-05-31
Perfect!  Thanks!

---

### Post by styleruk on 2009-06-25
Ah, the sudo rm command worked for me too.  That was driving me nuts.  Funny thing was I found the ./local/share/Trash folder.  tried to delete the files using sudo nautilus...and....well you probably guessed it...they came back each time with a slightly different name...LOL
This worked though
Thanks.
Si

---

### Post by bledsoe on 2009-06-25
Add my thanks as well.  This was really driving me crazy.

Can anyone explain why Ubuntu works this way?  In particular,
[LIST=1]
[*]When you delete a file as root (in Nautilus), why isn't the file "really" deleted?
[*]When you discover the /root/.local/share/Trash directory, why can't you "sudo nautilus" and carry out the delete operations graphically with root privileges?
[/LIST]

Thanks for any insight,

---

### Post by michy99 on 2009-06-25
To actually delete files in nautilus instead of sending them to trash, press Shift+Delete. This should work as regular user or root.

---

### Post by mcduck on 2009-06-25
> **bledsoe said:**
> Add my thanks as well.  This was really driving me crazy.

Can anyone explain why Ubuntu works this way?  In particular,
[LIST=1]
[*]When you delete a file as root (in Nautilus), why isn't the file "really" deleted?
[*]When you discover the /root/.local/share/Trash directory, why can't you "sudo nautilus" and carry out the delete operations graphically with root privileges?
[/LIST]

Thanks for any insight,

1. For the same reason why files aren't "really" deleted when you delete them as any other user. Most people seem to prefer having a trash bin available instead of really deleting things immediately when they delete them. Root is just a user like any other, so things work for root like they do for other users.

2. I've understood that there's some minor bug that causes this to fail. (And you shouldn't use "sudo nautilus, always use "gksudo" with graphical applications..)

---

