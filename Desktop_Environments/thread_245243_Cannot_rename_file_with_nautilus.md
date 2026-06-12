---
title: "Cannot rename file with nautilus"
date: 2006-08-27
forum: Desktop Environments
---

### Post by BIg2hd on 2006-08-27
Sry but I just been searching all weekend on my intial problem(Wine crashes when I click on Audio Tab, but I found solution) that need a quick fix so this thing won't gooble up another weekend.

Anyways it seems some folders and files(Imporatnt one is the wine folder in the usr/lib folder) that I right click on are all options(rename, delete, etc) grayed out and states I don't have permission(only one user and I assuming I'm the root) .  Did some googling and found the 'chmod' thing but it didn't work, any help would be appriecated thx in advance.

---

### Post by mgmiller on 2006-08-27
Open a terminal and type
```
sudo nautilus
```

After giving it your password, you will have a regular nautilus browser with root privileges.  Be careful!  You can really bork things up with this.  Make sure you are changing things that you understand.  As an aside, I just did the file rename thing to fix the audio tab causing wine to crash this morning.  It works.

---

