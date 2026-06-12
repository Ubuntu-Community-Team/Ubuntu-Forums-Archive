---
title: "permissions troubles"
date: 2009-03-19
forum: General Help
---

### Post by qwertyuiop96 on 2009-03-19
When I first installed Ubuntu, I had some user issues, and I solved them by creating A new account and deleting the old one and its group.  However, its folder in the /home directory stayed.  When I try to delete it, it says "Access denied"  I open the file browser as root, and it gives me the same thing, even for stuff in the plain old / directory.  This is soooo irritating!!  The folders are taking up space, and I just want to get rid of them! :mad:  Help please?  Running 8.10 intrepid ibex.

---

### Post by taurus on 2009-03-19
When you created a second account for you, did you remember to add yourself to group admin?  If you don't belong to group admin, you can't use sudo or gksudo since you don't have root privilege.

Applications -> Accessories -> Terminal
```
id
```

---

### Post by jlochhead on 2009-03-19
> **qwertyuiop96 said:**
> When I first installed Ubuntu, I had some user issues, and I solved them by creating A new account and deleting the old one and its group.  However, its folder in the /home directory stayed.  When I try to delete it, it says "Access denied"  I open the file browser as root, and it gives me the same thing, even for stuff in the plain old / directory.  This is soooo irritating!!  The folders are taking up space, and I just want to get rid of them! :mad:  Help please?  Running 8.10 intrepid ibex.

Yea the first thing to do is check whether you are in the sudoers file. If you are not (complete pain) you will have to grab a live cd and add yourself - or you will not be able to use root, which is obviously a major problem.

To test this type:

sudo -i

If you are in the sudoers file either you will become root or you will be told you are not in the sudoers file.

If you did manager to become root simply:

rm -r /home/<old-username>

exit

---

### Post by qwertyuiop96 on 2009-03-19
Thanks!!  That worked great- got rid of my stupid files right away.

---

### Post by hoomansoft on 2009-03-22
hi.I have a problem with sudoers file.last time whene my ubuntu works good, I creat a limited user, after this, my first user that i creat during ubuntu installation cant mount partitions &... whene i use sudo command this error return like this:hoomansoft2008 is not in sudoer files.
(hoomansoft2008 is my username)
please help!!!:(

---

### Post by taurus on 2009-03-22
> **hoomansoft said:**
> hi.I have a problem with sudoers file.last time whene my ubuntu works good, I creat a limited user, after this, my first user that i creat during ubuntu installation cant mount partitions &... whene i use sudo command this error return like this:hoomansoft2008 is not in sudoer files.
(hoomansoft2008 is my username)
please help!!!:(

Did you modify /etc/sudoers or somehow removed yourself from group admin?

```
id
```

---

### Post by hoomansoft on 2009-03-23
No, I don't change anything in sudoer file,I just made a new user and limited it but my first user can't run any program or commands that need to be admin. maybe I change my first user options in *user and groups*.

---

