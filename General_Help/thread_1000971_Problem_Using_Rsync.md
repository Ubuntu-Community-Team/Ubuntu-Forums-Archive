---
title: "Problem Using Rsync"
date: 2008-12-03
forum: General Help
---

### Post by CarlosinFL on 2008-12-03
I am trying to use rsync to copy all my files from one folder to another on the same system and seem to be having a problem. It's fairly simple.

I am taking everything from my /home/carlwill directory and using rsync to copy it to /media/usb. The problem I have is my home directory has tons of hidden files/folders that I want to 'exclude' from the rsync. I simply want just the hard data that I can see. None of the program files or folders that are associated with my user's home.

```
/usr/bin/rsync -ave --exclude .* /home/carlwill/ /media/usb/
```

This does not appear to be working for me as I am getting everything from .Mozilla and .Trash in my rsync so I keep starting over and I don't know what I am doing wrong.

Anyone care to help me?

---

### Post by Titan8990 on 2008-12-03
You only need the -e if you are using rsh to send the backup across the network. Also, the correct syntax would be:


```
/usr/bin/rsync -av --exclude=.* /home/carlwill/ /media/usb/
```

---

### Post by CarlosinFL on 2008-12-03
Thanks - that worked!

---

### Post by Titan8990 on 2008-12-03
Good to hear, don't forget to mark your thread as solved.

---

