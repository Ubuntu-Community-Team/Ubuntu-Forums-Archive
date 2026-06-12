---
title: "Where is the trash folder on Gutsy?"
date: 2009-02-06
forum: General Help
---

### Post by fogster on 2009-02-06
I know the answer: ~/.Trash -- but it's not there. Am I doing something foolish?

I'm recently logged-in. Recently-booted, even. Clicking the trash icon in the bottom-right tray brings up Nautilus at trash:///, which shows 26 items totally 18 MB. But:

```

fogster@t60:~$ ls -lh ~/.Trash
ls: cannot access /home/fogster/.Trash: No such file or directory
fogster@t60:~$ pwd
/home/fogster
fogster@t60:~$ ls -al *rash*
ls: cannot access *rash*: No such file or directory

```

Not that it would make sense anyway, but becoming root doesn't help find it. (And there's not a /root/.Trash either, even though fogster is the user that I'm logged in as.)

Am I overlooking something foolish? Has the directory moved?

I have a file in the trash owned by root, so I'm trying to pull up a shell and nuke it. But I can't find the directory, which is made even more aggravating by the fact that I'm pretty sure I know where it's supposed to be. :rolleyes:

---

### Post by finer recliner on 2009-02-06
I don't remember what version they made the switch, but the latest version of Ubuntu keeps the user's trash in ~/.local/share/Trash

try there!

---

### Post by drs305 on 2009-02-06
Since Hardy, the trash is located in *~/.local/share/Trash*  and root's trash is in */root/.local/share/Trash*

There are two subfolders: *info* contains information about where the files came from; *files* contains the actual deleted files.

For more information about Trash, read the tutorial whose link is in my signature line.

---

### Post by fogster on 2009-02-06
Ah-ha, that's it! Thanks guys. :D

(Oh yeah, I'm running Hardy, not Gutsy... Might have been good if I got that right, but you figured it out anyway. ;))

---

