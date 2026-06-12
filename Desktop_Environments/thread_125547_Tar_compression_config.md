---
title: "Tar compression config?"
date: 2006-02-04
forum: Desktop Environments
---

### Post by able on 2006-02-04
I am backing up the folder "Test" compressed to the file Test.tgz using the command "tar cvpzf Test.tgz". After a while i am running the same compression command. In the meanwhile I have deleted some folders and files in the Test-directory. My question is if the deleted folders and files still remains in the Test.tgz and if I have to adjust the command to achieve the compression-file as a mirror of the sorce-folder.

---

### Post by taurus on 2006-02-04
If you tar and compress that directory before you remove stuff in there, then it should still contain those files but if you tar and compress after you have removed those files, then those files are gone...

---

