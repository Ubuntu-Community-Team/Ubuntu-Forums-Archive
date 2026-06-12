---
title: "Strange File permissions for group user"
date: 2009-01-22
forum: General Help
---

### Post by Captain Giraffe on 2009-01-22
My goal is to add a user to www-data group to be able to edit web files from that account.
so I did a 
```
sudo usermod -a -G www-data my-user
```

```
cat /etc/group | grep my-user
```  yields something like
```
www-data:x:31:my-user
```
which looks fine to me.

www-data:www-data owns the web folder and all children.
the permissions in my web folder was changed with
```
sudo chmod -R g+w webfolder
```
and everything looks normal
rwxrwxr-x on the items in the folder and the folder itself.

Why can't my-user change anything in this folder?

/Cpt.G

---

### Post by amac777 on 2009-01-22
group settings are loaded at login so you probably need to logout and then login again in order to update that user's group permissions.

---

### Post by Captain Giraffe on 2009-01-22
amac777 Your answer is made of pure and solid Z=79. I bow and thank you.

---

