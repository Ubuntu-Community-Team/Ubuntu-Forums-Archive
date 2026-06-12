---
title: "Command to show users and their permissions"
date: 2009-01-28
forum: General Help
---

### Post by Simplemind169 on 2009-01-28
i'm learning ubuntu in class and one of our assignments is to display all the users and their permissions i cant seem to figure out the command to allow me to do this. Anyone have an idea?

---

### Post by HermanAB on 2009-01-28
$ sudo cat /etc/group

Cheers,

Herman

---

### Post by Simplemind169 on 2009-01-28
That gives me just the users i have set permissions i need to display as well

---

### Post by UbuntuNerd on 2009-01-28
For a list of users type:
```
cat /etc/passwd
```
and for a list of groups with the users that belong to each, type:
```
cat /etc/group
```
For access rights, you can use:
```
sudo find -user USERNAME /LOCATION
```

---

### Post by Simplemind169 on 2009-01-28
thanks for the reply but that command does not work. i am working with 8.10 so idk if that makes a difference but when i use the find command there is no display of the user permissions for example one user has a numerical permission of 750 and nowhere is that shown.

---

### Post by Wayne_V on 2009-01-28
I don't understand the question?   What user permissions do you want to display?

---

### Post by UbuntuNerd on 2009-01-28
yes be more specific?

---

### Post by Simplemind169 on 2009-01-28
well i ended up figuring it out instead of looking for the home directory permissions instead of the user

---

