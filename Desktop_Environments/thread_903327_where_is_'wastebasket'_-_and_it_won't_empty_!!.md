---
title: "where is 'wastebasket' - and it won't empty !!"
date: 2008-08-28
forum: Desktop Environments
---

### Post by neill on 2008-08-28
hi

in my wastebasket i have 2 folders that won't delete

if i try to do so i get a permissions error from nautilus

there is no .Trash folder in my or root's home directory !

where is 'wastebasket' located in the filesystem hierarchy and has anyone any tips for nuking these folders

(rm -rf ~/.Trash* don't work as i haven't got one !)

ta

/neill

---

### Post by arch0njw on 2008-08-28
It appears that it is possible to have more than one trash.  Those folders might also have different permissions on them.

This thread seems to have some helpful info (especially the "find" command):
[http://ubuntuforums.org/showthread.php?t=509596](http://ubuntuforums.org/showthread.php?t=509596)

You might want to try:
$ cd ~/.Trash
$ ls -la

>> who are the files owned by and what are the permits.  If they are owned by root, you could...

$ sudo rm -f [name of file here]
  OR
$ sudo rm -rf [name of dir here]

Note:  I am a fan of individually deleting things.  You could remove everything in the trash all at once with a sudo rm command, but that's a little too risky for my liking.

---

### Post by ad_267 on 2008-08-28
Your trash is in ~/.local/share/Trash/files if you're using 8.04.

---

### Post by neill on 2008-08-28
i am indeed 8.04 and when i ran rm -rf from the cli in ~/.local/share/.Trash/Files the stubborn little blighters vanish !!

ta da !

thanks

---

### Post by Kevbert on 2008-09-01
I notice that there's also some files in the ~/.local/share/Trash/info directory.  Is it OK to delete these ?

---

### Post by arch0njw on 2008-09-01
Yes.

Under the "Trash" directory, the "files" directory contains the files that were deleted.  The "info" directory contains files that specify the deletion date and the path where the file came from.  You can view the files in a text editor, "more" or "cat" them if you are curious.

---

