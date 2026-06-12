---
title: "Every user has access to all users files after separate /home partition"
date: 2006-08-12
forum: Desktop Environments
---

### Post by petri on 2006-08-12
I did an separate home partition as [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)
and reinstalled 6.06 LTS. Everything went fine the /home partition is in /etc/fstab and so on. 
But now every user I create has access to each others files and that shouldn't happen, right? Can someone help me? Do I need reinstall again?

---

### Post by Zdravko on 2006-08-12
I have the same problem. It is a bug. There is no way to protect personal data from other users under Ubuntu.

---

### Post by aysiu on 2006-08-12
It's not a bug. That's the way it's designed.

You can always *chmod* each directory as 700 if you want and then [change the default permissions](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9).

The way Ubuntu is set up, though, other users can read your files but not write to them.

---

### Post by petri on 2006-08-12
A bug? :D 

Well if Ubuntu is designed that way it's worse than it's competitors. Originally when I had /home in root partition the users couldn't even browse each others files. Or did I change it by myself at some point :rolleyes: 

Does Ubuntu really create a user with permission to the other users to browse and read the files? That's stupid 8-[ it can't be like that?

P.S. The link aysiu provided isn't a really an answer to my question. I'm simply creating users like /home/petri and /home/anette and so on. The link is although an solution to my future problem :D

---

### Post by aysiu on 2006-08-12
> **petri said:**
> 
Well if Ubuntu is designed that way it's worse than it's competitors. Originally when I had /home in root partition the users couldn't even browse each others files. Or did I change it by myself at some point :rolleyes: 

Does Ubuntu really create a user with permission to the other users to browse and read the files? That's stupid 8-[ it can't be like that? You must have changed something. The default is that everyone can read each other's files and not modify them.

---

### Post by petri on 2006-08-12
Yes, I must have logged in as the new user and changed permissions. It's been a while when I add new users so I don't remember.

I still think that's odd that anyone can see other users files by default. Those files should be a "secret" by default. :-s

---

### Post by aysiu on 2006-08-12
It's all a matter of opinion, and the developers don't agree with you.

I think ideally the default would be hidden files from other users. Then there should be an easy way to configure it so that it's totally unhidden (users can modify *and* read others' files) and that default permissions can be changed from the GUI with a few checkboxes.

Of course, denying write ability to users isn't real security. If they really want to read your files, they can boot into recovery mode and be root or boot up a live CD and view them. You can always encrypt files you don't want others to have access to.

If you want, you can file a bug report on it. I'm not sure the developers will be receptive to your suggestion.

---

