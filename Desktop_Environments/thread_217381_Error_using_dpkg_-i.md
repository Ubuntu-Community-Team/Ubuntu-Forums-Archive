---
title: "Error using dpkg -i"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Yumi on 2006-07-17
I try to install a .deb file with dpkg -i . I get the error "cannot access archive: no such file or directory"

What I am doing wrong?

Michael

---

### Post by mcduck on 2006-07-17
Sounds like you are not running the command in the same diractory where your file is. Either use the 'cd' command to move to the right place, or run the dpkg with full path to your file, like 'sudo dpkg -i /home/yumi/Desktop/file.deb'

---

### Post by Yumi on 2006-07-17
I would have liked this easy solution. But it persists. See the following dump:

michael@office-desktop:~/Desktop$ dir
gaim-openq-0.3.2                     skype-beta-1.3.0.30-1_i386.deb
michael@office-desktop:~/Desktop$ sudo dpkg -i skype-beta-1.3.0.30-1-i386.deb
dpkg: error processing skype-beta-1.3.0.30-1-i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-beta-1.3.0.30-1-i386.deb

Michael

---

