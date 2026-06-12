---
title: "NFS Displays Wrong Drive"
date: 2011-12-07
forum: Desktop Environments
---

### Post by kazhbu on 2011-12-07
First, I must say that I am a newbie with Linux.  I have installed Ubuntu 11.10 on my desktop and I am trying to share 5 external USB hard drives full of multimedia content to my Boxee.  I have been able to set up NFS file sharing using the exports file and the first two drives worked flawlessly.  Once I added a third drive, it shows on my boxee, but if I open the directory it shows the files from one of the first two drives.  I've tried swapping them out and no matter what I seem to do, the third drive will always show the contents from the first two even though the label is correct.  Is there some sort of limitation on the number of drives I can share over my network?  Here is the relevant contents of my exports file:  /media/&quot;Movies A-P&quot; *(rw,sync,no_root_squash,subtree_check) /media/&quot;Movies Q-Z&quot; *(rw,sync,no_root_squash,subtree_check) /media/&quot;TV A-L&quot; *(rw,sync,no_root_squash,subtree_check) /media/&quot;TV M-Z&quot; *(rw,sync,no_root_squash,subtree_check)   The first two (Movies A-P & Movies Q-Z) work pefectly.  The third (TV A-L) shows the contents of Movies Q-Z when I try and access it with my Boxee.  Any help would be greatly appreciated!

---

### Post by marinara on 2011-12-08
sounds like a typo.
post your whole exports file to here and to pastebin

---

