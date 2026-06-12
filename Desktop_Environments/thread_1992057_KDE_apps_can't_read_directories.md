---
title: "KDE apps can't read directories"
date: 2012-05-31
forum: Desktop Environments
---

### Post by JuhazOne on 2012-05-31
Today KDE stopped working for my current user and I renamed ~/.kde away so that KDE would create a new directory when I log in next time. It did, but now KDE apps can't read directory listings. For example, if I launch Dolphin it won't show any files in my home directory or the root directory. However, it does display some items under Network and it does show the contents of Trash.

Most file dialogs that I open also won't show any files, instead they display an error dialog that says:

```
Could not start process Unable to create io-slave:
klauncher said: Error loading 'kio_file'.
.
```

It's curious though that the file open dialog is able to suggest completions for paths I start typing in the file name box. I still can't use the file dialog to choose a file though.

While searching the web for help someone suggested to try something like this:

```
$ echo foobar > foobar
$ kioclient cat file://foobar
kioclient(3399): couldn't create slave: "Unable to create io-slave:
klauncher said: Error loading 'kio_file'.
"
```

The message printed by kioclient is also shown by Dolphin and the file open dialogs.

Trying to open a file in Gimp seems to work, so I assume that this is a problem with KDE (that GTK apps aren't affected).

Moving ~/.kde again away and starting fresh didn't help. Creating a new user and logging in to KDE as that user didn't help. Any suggestions on how to fix this?

I'm using Kubuntu 11.10. I will probably upgrade to 12.04 sometime soon but the exact moment is not something I can decide and I'd rather have a working system until I can upgrade.

uname -a prints:
Linux myhostname 3.0.0-20-generic #34-Ubuntu SMP Tue May 1 17:24:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by JuhazOne on 2012-08-01
I didn't find a solution but instead I started from scratch with Kubuntu 12.04. I kept my home directory so apperently the problem was somewhere outside it.

---

