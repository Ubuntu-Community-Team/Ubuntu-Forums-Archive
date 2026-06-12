---
title: "Cyrillic names in rsync and getfacl, getattr"
date: 2010-02-19
forum: Desktop Environments
---

### Post by alikthename on 2010-02-19
Could anyone please exlpain me why address 

/home/domain/shares/&#1054;&#1073;&#1097;&#1077;&#1089;&#1090;&#1074;&#1077;&#1085;&#1085;&#1072;&#1103; 

is displayed as 

home/domain/shares/\320\236\320\261\321\211\320\265\321\201\321\202\320\262\320\265\320\275\320\275\320\260\321\217

in getfacl's output.

Here is the whole line and output

```
home/pdcadmin# getfacl /home/domain/shares/&#1054;&#1073;&#1097;&#1077;&#1089;&#1090;&#1074;&#1077;&#1085;&#1085;&#1072;&#1103;
getfacl: Removing leading '/' from absolute path names
# file: home/domain/shares/\320\236\320\261\321\211\320\265\321\201\321\202\320\262\320\265\320\275\320\275\320\260\321\217
# owner: root
# group: Domain\040Admins
user::rwx
user:Sergey_K:rwx
user:Konstantin_Sh:r-x
user:Natalia_D:r-x
group::rwx
group:Domain\040Admins:rwx
group:Domain\040Users:r-x
mask::rwx
other::rwx
default:user::rwx
default:user:Sergey_K:rwx
default:user:Konstantin_Sh:rwx
default:user:Natalia_D:rwx
default:group::rwx
default:group:Domain\040Admins:rwx
default:mask::rwx
default:other::---
```

---

