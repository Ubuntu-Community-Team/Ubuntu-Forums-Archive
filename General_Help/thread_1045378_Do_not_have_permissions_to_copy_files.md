---
title: "Do not have permissions to copy files"
date: 2009-01-20
forum: General Help
---

### Post by oscarinabox on 2009-01-20
I am trying to copy files from my Documents folder to /usr/local/games/doom3/base/ and it is saying i dont have permission to do so. I am fairy new to ubuntu. I have only been using it for a couple of months.

---

### Post by inadaze on 2009-01-20
You could try 
```

sudo cp filename destinationFolder

```
it will then prompt you for a user password (the one you log into with)

"sudo" is like telling the computer that "I am the boss and here is my proof".  But be careful, if the computer is telling you that you don't have permissions it is because the file or folder is owned by other user (the computer/root or someone like that).  It could be that you are not suppose to move that file (or you should not move things to that folder) and you could mess things up.  Just be sure before you move files that you know that it is safe to move the file and it is safe to put it in that folder.

Cheers,
Jay

---

