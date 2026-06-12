---
title: "File deletion error..."
date: 2009-01-28
forum: General Help
---

### Post by Gizenshya on 2009-01-28
I have a big folder full of files I want to delete.  but they won't delete.

it returns "Error removing file: Permission Denied."

So, I tried restoring all of them, and meticulously changing permissions for each file (because the set permissions for subfolders and files just doesn't work at all).

then I deleted them... they deleted.  but the original ones I deleted are STILL in my trash :(

how do I get them out?  how can I not have permission?  is there a sudo delete for trash?

---

### Post by Boomhauer on 2009-01-28
run this from a terminal
```
sudo rm -rf /home/YourUserName/.local/share/Trash/files
```
EDIT: and in the future if you want to make a whole folder owned by yourself you can run ```
sudo chown -R username:username /path/to/folder
``` changing both instances of username to your personal username.  you dont want to go all willy nilly changing ownership of system files though!

---

### Post by Gizenshya on 2009-01-28
thank you!!!

worked perfectly :D

---

### Post by Gizenshya on 2009-01-28
and they weren't system files, just some random backed up files I'd copied from a backup dvd.  for some reason they kept the read-only file permissions

also.. isn't there a thank button somewhere?  I thought I've seen them before on this forum.. but I can't find one to thank you haha

---

### Post by Boomhauer on 2009-01-28
i didnt mean to suggest that they were.  ive have seen people chown their whole system thinking it would make things easier before so i was just giving a little caution :)

---

### Post by Gizenshya on 2009-01-28
ahh, gotcha.  I'll keep that in mind :)

---

