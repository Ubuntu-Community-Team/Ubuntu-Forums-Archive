---
title: "file permissions"
date: 2009-06-11
forum: General Help
---

### Post by lex1 on 2009-06-11
Permissions are set like so

: -rwx------ 1 www-data root 0 2009-06-11 14:28 nontmp

they need to be like this  

: drwx------ 1 www-data root 0 2009-06-11 14:28 nontmp

what should I type on command line

lex1;)

---

### Post by ActiveFrost on 2009-06-11
```
sudo chmod 701 /home/mydir
```

---

### Post by ibuclaw on 2009-06-11
> **lex1 said:**
> Permissions are set like so

: -rwx------ 1 www-data root 0 2009-06-11 14:28 nontmp

they need to be like this  

: drwx------ 1 www-data root 0 2009-06-11 14:28 nontmp

what should I type on command line

lex1;)

That isn't a permissions issue. What you should really be doing is removing the **file** and creating a **directory** in it's place instead...

```
sudo rm nontmp
sudo mkdir nontmp
sudo chown www-data:root nontmp
sudo chmod 700 nontmp
```

Regards
Iain

---

### Post by drubin on 2009-06-11
> sudo chown www-data:root nontmp


Just for reference having this type of ownership makes no sense. www-data is the owner but group access is root?

I think the OP is meaning to do. Owner is root but www-data is the group and has permissions as such.
```
sudo chown root:www-data nontmp
```

---

### Post by andersbk on 2009-06-11
> **lex1 said:**
> Permissions are set like so

: -rwx------ 1 www-data root 0 2009-06-11 14:28 nontmp

they need to be like this  

: drwx------ 1 www-data root 0 2009-06-11 14:28 nontmp



There is no difference in the permissions above.

One is a file: -rwx

The other a directory: drwx

Apples and Oranges.

.

---

