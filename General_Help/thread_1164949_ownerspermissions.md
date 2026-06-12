---
title: "owners/permissions"
date: 2009-05-20
forum: General Help
---

### Post by lex1 on 2009-05-20
how do i create a directory called www/cgi-data and another calledwww/cgi-data/nontmp?
how do i make cgi-data the owner of nontmp and set permissions to 0700?

lex1:p

---

### Post by mcduck on 2009-05-20
```
sudo mkdir /var/www/cgi-data
sudo mkdir /var/www/cgi-data/nontmp
sudo chown cgi-data:cgi-data /var/www/cgi-data/nontmp
sudo chmod 0700 /var/www/cgi-data/nontmp
```
..or just run "gksudo nautilus" and do the same stuff with the file manager. ;)

---

### Post by lex1 on 2009-05-20
when i ran
sudo chown cgi-data:cgi-data /var/www/cgi-data/nontmp
i got
invaild user cgi-data:cgi-data

---

### Post by mcduck on 2009-05-20
> **lex1 said:**
> when i ran
sudo chown cgi-data:cgi-data /var/www/cgi-data/nontmp
i got
invaild user cgi-data:cgi-data

you must have the user & group "cgi-data" to do that.

Based on your private message you actually want that directory to be owned by "www-data", not "cgi-data", so use this command instead:

```
sudo chown www-data:www-data /var/www/cgi-data/nontmp
```

The basic syntax for chown is "chown *user*:*group* */path/to/your/target*"

---

### Post by albinootje on 2009-05-20
For the OP, and anyone else who didn't know this yet.

Instead of this :
```

sudo mkdir /var/www/cgi-data
sudo mkdir /var/www/cgi-data/nontmp

```
This could have been used :
```

sudo mkdir -p /var/www/cgi-data/nontmp

```
The parameter "-p" automatically creates all non existing sub directories with that command.

---

### Post by lex1 on 2009-05-20
thanks for your posts ;

sudo chown www-data:www-data /var/www/cgi-data/nontmp

yes that worked thankyou.
what about the last line

sudo chmod 0700 /var/www/cgi-data/nontmp

will that be diffrent from what you siad in the first post?

thanks

lex1:p

---

### Post by mcduck on 2009-05-20
> **lex1 said:**
> 
what about the last line

sudo chmod 0700 /var/www/cgi-data/nontmp

will that be diffrent from what you siad in the first post?

thanks

lex1:p

no, that's the same. Chmod only changes the permissions, regardless of user/group owning the directory. So having different owner for the directory doesn't change that command on any way.

---

