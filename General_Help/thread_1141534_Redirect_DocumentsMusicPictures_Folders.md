---
title: "Redirect Documents/Music/Pictures Folders"
date: 2009-04-28
forum: General Help
---

### Post by eyescovered on 2009-04-28
i keep all my stuff on an external hard drive. is there a way so that when you go to your home folder you can redirect the music folder (for example) to go to an external device?




EDIT: just found it on my own. you can edit the bookmarks and put whatever path you want.

---

### Post by Nepherte on 2009-04-28
For the record, you could have also created a symbolic link that links to another directory/file. An example:
```
ln -s /media/external/Documents /home/username/Documents
```
This will create a directory Documents in your home directory that will direct everything to /media/external/Documents. It's as if /media/external/Documents is located at /home/username/Documents.

---

