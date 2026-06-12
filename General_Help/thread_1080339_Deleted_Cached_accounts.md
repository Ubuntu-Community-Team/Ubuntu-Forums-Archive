---
title: "Deleted Cached accounts??"
date: 2009-02-25
forum: General Help
---

### Post by johnson8707 on 2009-02-25
So in the home folder, the cached accounts of users logging in are starting to build up. When I go to delete the folders using the "rmdir" command it says that the directory is not empty. But I can't see all of the files and folders within it because i am not logged in as that person. (I am trying to delete them using the sudo command in terminal)


Is there anyway to just delete the entire folder? Even if it does have folders and files within it?


THANKS!!

---

### Post by taurus on 2009-02-25
```
sudo rm -rf directory_name
```
Just be real _careful_ with the -rf oprion.  So, make sure you get the directory_name right because there is no way to recover what you delete!

---

