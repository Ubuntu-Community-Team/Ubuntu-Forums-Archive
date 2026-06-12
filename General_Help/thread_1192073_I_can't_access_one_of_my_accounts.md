---
title: "I can't access one of my accounts"
date: 2009-06-19
forum: General Help
---

### Post by Tiber828 on 2009-06-19
Basically, a couple of weeks ago I manually changed permissions for a couple of folders from r x to rwx for others on one of my accounts (both of which have sudo/admin privileges) and shut down the computer. The next day I couldn't log in to that account and was prompted with rescue mode (which didn't open). I can log in to my other account and would chmod of the folders causing the problems but I don't know which ones they are. Is there any way to figure out which folders I need to change back to just readable?

---

### Post by pytheas22 on 2009-06-19
What is the exact error message that you receive when trying to log into the account?  And what is the output of the command:
```

ls -la /home/username
```

for that account (where 'username' is replaced with the appropriate name).

Also, you're getting to the Gnome login screen where you type your username and password, correct?  There's no problem booting the system itself?

---

