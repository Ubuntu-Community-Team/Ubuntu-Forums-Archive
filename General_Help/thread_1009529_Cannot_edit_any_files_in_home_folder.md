---
title: "Cannot edit any files in home folder"
date: 2008-12-12
forum: General Help
---

### Post by cylux on 2008-12-12
Hello ladies and gentlemen. 

I've got a (hopefully) quick question for you, any help is appreciated.

Within my home folder, I find that I cannot create, write to or save over any files.

So if I were to open a terminal window and do

```
nano -w ~/hello.txt
```

for example

I get something that looks like this

```
Error reading /home/cylux/.nano_history: Permission denied

Press Enter to continue starting nano.
```

I can press enter and view the file, however, when it comes to saving, I get permission denied.

In fact in order for me to edit ANY file within my home directory, I must prepend the nano command with 'sudo'

Why is this the case? If this is some whack security feature, how do I disable it?

Edit: UPDATE

Been playing around, maybe it's due to this file being owned by root? How do I change it?

```
-rw-------  1 root  root         35 2008-12-12 18:09 .nano_history
```

---

### Post by dexter on 2008-12-12
Try reclaiming all files in your home directory:
```
sudo chown cylux:cylux -R .
```

---

### Post by LoneWolfJack on 2008-12-12
```
sudo chgrp usergroup filename
```

---

### Post by Babarock on 2008-12-29
sudo chmod 666 .nano_history 

It worked fine for me.

---

