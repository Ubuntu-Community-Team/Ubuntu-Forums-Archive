---
title: "Is there a way to password protect folders in Ubuntu?"
date: 2006-01-15
forum: General Help
---

### Post by Protex on 2006-01-15
Hey there guys, I have a couple folders with some sensitive information. Is there a way to password protect them?

Thanks in advance.

---

### Post by aysiu on 2006-01-15
One of these two threads *may* help, but I don't know:
[http://ubuntuforums.org/showthread.php?t=25848](http://ubuntuforums.org/showthread.php?t=25848)
[http://ubuntuforums.org/showthread.php?t=89354](http://ubuntuforums.org/showthread.php?t=89354)

---

### Post by Mr_Grieves on 2006-01-15
By restricting permissions to folders and creating a user per person that uses that system and activating a password protected screensaver when away from your computer, you should be fine :)

---

### Post by RAOF on 2006-01-15
Depending on how serious you want to be, you can restrict access to the folder to only you (and root) by changing the permissions.  If you remove all permissions for everyone but you (chmod -R go-rwx the_folder_you_want_to_protect), users won't be able to "cd" into the directory, and will be unable to read or write the files in it.

This is pretty simple, and quite easy to get around - anyone with an admin account (sudo access) can still access those files.  

If you really want to protect the contents of the folder, you'll need to encrypt it, and I'm not sure how.

---

### Post by Protex on 2006-01-15
[QUOTE=RAOF]Depending on how serious you want to be, you can restrict access to the folder to only you (and root) by changing the permissions.  If you remove all permissions for everyone but you (chmod -R go-rwx the_folder_you_want_to_protect), users won't be able to "cd" into the directory, and will be unable to read or write the files in it.

This is pretty simple, and quite easy to get around - anyone with an admin account (sudo access) can still access those files.  

If you really want to protect the contents of the folder, you'll need to encrypt it, and I'm not sure how.[/QUOTE]

Your method seems best right now, I've done it and the folder is locked. Now assuming I want to open it and view the documents inside, how would I go about doing that?

---

### Post by RAOF on 2006-01-15
[QUOTE=Protex]Your method seems best right now, I've done it and the folder is locked. Now assuming I want to open it and view the documents inside, how would I go about doing that?[/QUOTE]
Hmmm.  As I understand it, my command should have removed everyone else's access to your directory.  You should still be able to access it normally.  If you run a "ls -lah" in the directory containing the locked directory, who is the owner?
```
drwx------  3 chris chris  264 2006-01-16 15:20 decoder
```
Is a sample line of output, showing "chris" as the owner.

Anyway, if you can't, you can just run "sudo chmod -R ug+rwx the_folder_name" and get the full access back again.

---

### Post by Protex on 2006-01-15
[QUOTE=RAOF]Hmmm.  As I understand it, my command should have removed everyone else's access to your directory.  You should still be able to access it normally.  If you run a "ls -lah" in the directory containing the locked directory, who is the owner?
```
drwx------  3 chris chris  264 2006-01-16 15:20 decoder
```
Is a sample line of output, showing "chris" as the owner.

Anyway, if you can't, you can just run "sudo chmod -R ug+rwx the_folder_name" and get the full access back again.[/QUOTE]

Thanks a lot!

---

