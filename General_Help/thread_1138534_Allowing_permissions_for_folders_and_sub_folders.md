---
title: "Allowing permissions for folders and sub folders"
date: 2009-04-26
forum: General Help
---

### Post by whaler1 on 2009-04-26
Hi, I am trying to allow all users permission to some folders and sub-folders in ubuntu 8.10.  When I open up permission on the main folder with
 
chmod a+rw '***folder_name'***
**** 
the main folder opens up but then all the sub-folders get locked.  Is there any way to open up all the sub-folders, sub-sub-folders etc in a simple fashion.
 
Thanks

---

### Post by spiderbatdad on 2009-04-26
the easiest solution might be to change the group the folders belong to and add user to that group...then chmod g+rw
Or you could use a wildcard * after the directory name chmod -R a+rw /directory/*

---

