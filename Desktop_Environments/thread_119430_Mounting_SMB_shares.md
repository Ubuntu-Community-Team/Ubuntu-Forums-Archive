---
title: "Mounting SMB shares"
date: 2006-01-19
forum: Desktop Environments
---

### Post by geekphreak on 2006-01-19
I know this was asked a lot, but I can't figure out how to get it to work...
Say a user's SMB share is \\server\user$ on Windows. I think one can get to it by typing in smb://user:password@server in Konqueror. What I would like to do is create a link on every user's desktop that would go to their SMB share on a Windows server. I tried playing with fstab entries, but it did not work. Is there a way I can specify a generic path in fstab entry like //server/user, where user would be any user who logs in, and what would I need to specify in the link to SMB share in order for any user to just double-click and mount their SMB share?
I tried some things, but they did not work. Any help would be appreciated.

---

### Post by schilcha on 2006-01-20
I don't know if/how to do that via fstab. Therefore, I'll propose a workaround:

Since you're satisfied with mounting a share at login, you can write a simple shell-script that is executed automatically. e.g.
```

smbmount //server/$USER $HOME/server  -o credentials="$HOME/.smb.secrets"

```
You can also create a similar script to be executed at logoff. 

Good Luck!

---

