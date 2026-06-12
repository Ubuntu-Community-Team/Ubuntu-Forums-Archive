---
title: "Help, Files are gone, but i get no space!"
date: 2006-01-09
forum: General Help
---

### Post by Ocxic on 2006-01-09
i recently deleted a bunch of files/folders from my main drive that i was using for storage. the folders were all in the root of the drive (ie: /Movies, /Music....)
all totaling about 110GB of data, now i clicked onto move to trash, but nothing ever went tino my trash, this files are no longer on my hard drive, or so nautilus (and the terminal) says, but there was no space cleared on the drive, i still only have 20GB left, when i should have around 100GB after deleting thos files/folders what gives?

---

### Post by earobinson on 2006-01-09
check the drives in question for a .trash (or something like that file) to check if they are gone, it could be some weird bug

---

### Post by kaamos on 2006-01-09
Check for hidden folders on the drive. Press control+h in nautilus or the command "ls -la" in terminal.

---

### Post by Ocxic on 2006-01-09
Ok, I did that and found 3 .trash folders
.trash-root  (this has my entired hard drive in it?!?!?!?!?)
.trash-admin
.trash-ubuntu

and none of my suposedly deleted files are in there. I also did a search and it found nothing.

---

### Post by dcstar on 2006-01-09
[QUOTE=Ocxic]Ok, I did that and found 3 .trash folders
.trash-root  (this has my entired hard drive in it?!?!?!?!?)
.trash-admin
.trash-ubuntu

and none of my suposedly deleted files are in there. I also did a search and it found nothing.[/QUOTE]
Sometimes you can move things into Trash as a root user, and then you cannot see them as a "normal" user.

Start a root Nautilus session with the following command:

gksudo "nautilus --browser %U"

and have a look in those trash folders then.

You can also use the "File-Empty Trash" function to empty the root trash from this window (and free up disk space).

---

### Post by earobinson on 2006-01-10
also if you have 2 hd's each hd will have its own .trash files

---

### Post by Ocxic on 2006-01-10
it is fixed, thanks guys. it was in the /root/.trash  folder

---

### Post by earobinson on 2006-01-11
good to know, you must have been root when you removed the files.

---

### Post by Thirsteh on 2006-01-11
You shouldn't do something like that as root, glad it worked out for ya though. :)

---

### Post by Ocxic on 2006-01-11
had no choice, the files were locked for some reason, it's all good now tho

---

