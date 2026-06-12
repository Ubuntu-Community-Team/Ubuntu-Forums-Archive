---
title: "password protected dir?"
date: 2006-08-13
forum: Desktop Environments
---

### Post by lonelypauly on 2006-08-13
is it possible to password protect a folder on my desktop?

---

### Post by chrisccoulson on 2006-08-13
I'm not sure if it is possible to password protect a folder. but you could make root the owner of the folder, then do a chmod -R 700 <folder> and use sudo to access it.

---

### Post by jordilin on 2006-08-13
> **chrisccoulson said:**
> I'm not sure if it is possible to password protect a folder. but you could make root the owner of the folder, then do a chmod -R 700 <folder> and use sudo to access it.

It's impossible to do
```
sudo cd directoryname
```
when directoryname is a folder owned by root with 700 permissions. You must be root by doing
```
sudo -i
```
The only way to password protect a directory is encrypting it.

---

### Post by ardchoille on 2006-08-13
I have several users on my system and I have verified that this procedure will disallow them from seeing the contents of a folder.

chown user:user /path/to/directory
chmod 700 /path/to/directory

That's it. Everything in that directory, and its subdirectories, will be "off limits" to all other users except root. I logged into a couple of the other user accounts and tried to cd to that directory and I couldn't (nautilus couldn't get there either), I also tried to cd to a subdirectory of that directory and couldn't. Likewise for opening pics, files, ect. from that directory. It's only available to myself and root.

Not sure if this was your goal, but it does work.

---

### Post by jpkotta on 2006-08-13
If you don't want other users to be able to access a directory, simply do```
chmod -R go- my_directory
```  Then only your user (and root) can access it and all of the files inside.  

If you want stronger protection, then encryption is the way to go.

---

### Post by ardchoille on 2006-08-13
Yeah, if you don't want someone with a LiveCd to be able to view that directory and its contents, you might check into encryption.

---

