---
title: "Changing Desktop folder permissions for new files"
date: 2008-12-12
forum: General Help
---

### Post by ztrange on 2008-12-12
I want all the files created in the desktop to have different permissions. Why?

When firefox starts a download of lets say file.zip it creates the file.zip and a file.zip.part. Then, when firefox crashes, or its closed before the download is finished, when it is opened back, it resumes the download or at least it is supposed to do it. 

The problem is that when firefox tries to access the file to resume it, the file has a different permission level and cannot use it so the download gets corrupted and fails.

If I change the permissions of the file before opening firefox back, Firefox is able to resume the download without problems. So, my question is

Is there a way to make the files have the right permissions in order to firefox be able to resume any downloads?

Thanks

---

### Post by ztrange on 2008-12-12
bump!

---

### Post by soro2005 on 2008-12-12
The files get the permissions from the program that creates them (Firefox in your case), and ownership from the user that runs the program that creates them.

How exactly do you have to manually change permissions to accomplish what you want to accomplish? What are the permissions you have to apply to the files?

---

