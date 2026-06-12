---
title: "In &quot;Files&quot; I can't Backspace to return back in UBUNTU 13.04"
date: 2013-05-26
forum: Desktop Environments
---

### Post by UnUnlucker on 2013-05-26
Afetr Updating Ubuntu from 12.04 to 13.04 I can't use Backspace for returning back in folders. How can I make Backspace making this operation

---

### Post by vanadium on 2013-05-26
[http://askubuntu.com/questions/287936/changing-nautilus-key](http://askubuntu.com/questions/287936/changing-nautilus-key)

---

### Post by UnUnlucker on 2013-05-26
I can't find this ".config" It just doesn't exist there.

---

### Post by vanadium on 2013-05-28
In your home folder, find .config (first show hidden files by clicking "show hidden files" or by pressing Ctrl+H). There, you will find the "nautilus" folder and the "accels" file.

It is quicker, though, to open a terminal and immediately load the file in the editor with the command
```

gedit ~/.config/nautilus/accels

```

---

### Post by UnUnlucker on 2013-05-30
Wow, a lot of new experience, Thanks that worked) But after restarting of computer only

---

### Post by UnUnlucker on 2013-05-30
Guys, how can I make this thread solved?

---

### Post by vanadium on 2013-06-01
Not sure, but I think you edit your first post, then add '[solved]" in front of the topic title.

---

### Post by stylintile on 2013-06-01
Hi,
     To mark this thread solved, go to your first post, and on the bottom right of it select "Edit Post".  Then change the prefix (where you selected "ubuntu") to "Solved".
Glad you got it solved

---

