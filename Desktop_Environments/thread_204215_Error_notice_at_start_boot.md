---
title: "Error notice at start boot?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Ted D. on 2006-06-26
I am getting the following notice at boot/start.
Is a fault and can it be corrected?

notice: "$Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User $Home directory must be owned by the user and writable by other users."

I take permissions have to be changed for $Home/.dmrc.. What are 644 permissions?

Assistance please and Thanks in advance

---

### Post by GarlicFish on 2006-06-26
check out 
man chmod

basically files have permissions for user, group, others
Permissions are a bitmap rwx 
read = 4
write = 2
execute = 1

so 644 is
user = 4 + 2 = read + write
group = 4 = read only
others = 4 = read only

you can change the permissions on the file with 
chmod 644 filename

---

