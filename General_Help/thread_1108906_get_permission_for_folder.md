---
title: "get permission for folder"
date: 2009-03-28
forum: General Help
---

### Post by annebo on 2009-03-28
I am trying to retrieve docs from a former mac hdd. Ubuntu recognizes the drive but I cannot access the documents. I tried to change ownership..no success...I don't know much about commands...learning...any help? thanks...

---

### Post by mikewhatever on 2009-03-28
Generally speaking, a file may be unaccessible due to permissions or because the system can't mount a partition. The latter is usually the case if the file system is damaged and has nothing to do with permissions, and, different tools are needed. The question is, why can't you access the file. What errors do you get? How do you know it's because of permissions?

---

### Post by annebo on 2009-03-28
When I try to open a folder under the user name it says You do not have the permissions necessary to view the contents of "Documents".When I right click and go to properties/permissions it says you are not the owner,so you can't change those permissions..
However I just tried right now to open the doc folder under a user name(3 of them) and I can open it but when I try to copy it , it's denied...
I also tried the command : gksudo nautilus and got this answer:
** (nautilus:9057): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
Sorry if this looks like a mess...!!!

---

### Post by annebo on 2009-03-28
well, after trying different things I finally could access all the files that were on the desktop (which are the most important) and saved them in a folder in Ubuntu...(but don't ask me how...I am still trying to find out...and learning...!!!)
So I guess I'll close this thread and thank the people who answered...

---

