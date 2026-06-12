---
title: "permissions of &quot;Filesystem&quot;"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Chase48 on 2006-08-06
how do i make it so i can read and write to the hard disk "Filesytem"?

---

### Post by Sutekh on 2006-08-07
The 'Filesystem' is off limits to an ordinary user to prevent them causing damage to the system files. You can change this, but I'd really recommend against it. In fact, I think I have seen cases where just even changing the access to the main filesystem has caused errors in itself.

An ordinary user can go nuts inside their 'home' folder - /home/username/, however outside of that to modify system files or create new files, the user must be able to have extra priveleges.

The way to do this is to use the command **sudo**.  You can get a good read from [Ubuntu Help - RootSudo]("https://help.ubuntu.com/community/RootSudo").

Basically from the command line, the command **sudo** allows an ordinary user to run a command as the user root (who has total access).

If you wish to browse your files as root,you can run Nautilus, the file browser as root, using
```
gksudo nautilus
```from the run dialog (Alt+F2) or a Terminal (Applications -> Accessories menu)

Is there any particular reason that you need access to the filesystem?  Perhaps it's something we can help with.

---

