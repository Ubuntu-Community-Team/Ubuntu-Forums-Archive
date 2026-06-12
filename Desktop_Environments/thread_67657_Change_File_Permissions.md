---
title: "Change File Permissions"
date: 2005-09-20
forum: Desktop Environments
---

### Post by karuptdata on 2005-09-20
I jave a few files that were created under the root user and i would like to have standard user have permissions to write change etc..however when i change it under permissions logged in as root everything looks fine..but still all files are locked out from regular user any ideas??

---

### Post by aysiu on 2005-09-20
Type this into a terminal ```
man chown
```

---

### Post by karuptdata on 2005-09-21
i typed that into terminal and i have no idea where to go from there any additional ideas?

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=karuptdata]i typed that into terminal and i have no idea where to go from there any additional ideas?[/QUOTE]
Well, I believe you have two choices:
1) root continues to own the file, but you change the permissions so that *all* other users have permission to read and write to the file.

2) You change the owner/group of the file to a specific owner or group you want to have access.

This can be accomplished through the gui.  From the terminal, the command "chmod" changes permissions, and "chown" changes ownership.

Example: If your file is "foo":
```
$ sudo chown user foo
``` 
Changes the owner of the file to "user".

---

### Post by karuptdata on 2005-09-21
Great let me ask this is there a way to change multiple files within the directory for instance the name of the dir is Music but it contains roughly 1,000 songs, please tell me i dont have to do each one by one..

---

### Post by omp on 2005-09-21
[QUOTE=karuptdata]Great let me ask this is there a way to change multiple files within the directory for instance the name of the dir is Music but it contains roughly 1,000 songs, please tell me i dont have to do each one by one..[/QUOTE]

this is when the * comes in handy...

for example, music/*.mp3  would mean all 'mp3' files in the folder 'music'

---

### Post by doclivingston on 2005-09-21
"chown -R user music/" will change the owner of the music folder, and everything under it (-R tells it to perform the operation recursively)

---

### Post by karuptdata on 2005-09-21
ok so i did what you told me however it changed some of the files but not all....maybe logout correct the issue?

---

### Post by omp on 2005-09-21
[QUOTE=karuptdata]ok so i did what you told me however it changed some of the files but not all....maybe logout correct the issue?[/QUOTE]
If you used the example I gave, it will just work on mp3 files in just that one directory.. (I wanted you to get familiar with *)

However, doclivingston's example should work just fine.

---

