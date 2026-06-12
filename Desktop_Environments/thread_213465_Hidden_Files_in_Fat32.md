---
title: "Hidden Files in Fat32"
date: 2006-07-11
forum: Desktop Environments
---

### Post by ace2005 on 2006-07-11
How do i make files that appear hidden in windows appear hidden in linux, i'm using konqueror to browse the drive. I have lots of portable apps on it and so it has a lot of folders that i want hidden. Is this even possible?

Thanks for any help you can give.

---

### Post by john_spiral on 2006-07-11
filenames with a period before the file name keep them hidden.

e.g 

.something

will be hidden

---

### Post by ace2005 on 2006-07-11
I know that but if i change the filenames the programs won't work any more :(  so i can't put a . in front of it. Sorry if i wasn't clear

---

### Post by john_spiral on 2006-07-12
How about changing the read permissions on the directory/file, I'm not sure if the permissions are stored in one location under Linux or in the actual file itself?

Will changing the read permissions on a fat mounted windows file or directory have an effect on the usability of the file under windows?

anyone?

---

### Post by bom28 on 2006-07-13
Sorry, but I think the permissions for a mounted fat32 partition are the same for every file and folders, they are set in the mount options/fstab.

I don't think you can do what you want to do.
Or maybe encrypting the files...

---

