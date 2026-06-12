---
title: "How to recursively delete own directories which contain other peoples directories?"
date: 2009-01-14
forum: General Help
---

### Post by Ramsed on 2009-01-14
How to delete my own world-writable directories if some other user has put dirs and files inside? 

First create directory and make the directory world-writable by everybody.

  me@# mkdir mydir
  me@# chmod 777 mydir

Than login as another user, and put some things in mydir:
  user@# mkdir mydir/user_dir
  user@# touch mydir/file1
  user@# touch mydir/user_dir/file2

Now, I am unable to delete my own directory mydir. 

  user1@# rm -Rf mydir
  rm: cannot remove `mydir/user_dir/file2': Permission denied

I can delete the mydir/file. But since I have no write-permissions on directory user_dir, I can not delete user_dir/file2, and therefore I cannot delete the user_dir. This makes it impossible to delete my own directory mydir.

What to do, how to delete this directory. It seems that if a user (even by accident) makes directories in his home directory world-writable, it is impossible without admin-access to delete this directories if somebody happens to have put directories inside.

Thanks,
Sander

---

### Post by Woody1987 on 2009-01-14
sudo rm -r mydir

---

### Post by hyperdude111 on 2009-01-14
sudo nautilus

It opens up the file manager as super user you should have all privilages.

---

### Post by Ramsed on 2009-01-14
> **Woody1987 said:**
> sudo rm -r mydir

Sudo implies some admin-access. I would like to be able to delete my own directory "on my own".

---

### Post by redilyn on 2009-01-14
```

sudo chown $user -R /mydir

sudo chmod 777 -R /mydir

rm -R /mydir

```

---

### Post by wootah on 2009-01-14
> **redilyn said:**
> ```

sudo chown $user -R /mydir
 
sudo chmod 777 -R /mydir
 
rm -R /mydir

```
You guys have all missed the point. He wants to be able to remove his own directory without the use of root/sudo. Since the directory is in his own folder, but created by another user, that user can set privs on that directory and forces the parent to be unable to delete that directory.
 
Thread op: What you need to do is set the setgid bit on the directory to force the group owner of the parent folder to be the same as the subfolders along with the files in that directory. You should be able to delete anything now that has been modified, or at least change the privileges because you are in that group (ie: the person who created the file or directory--THEIR GROUP, is not applied to the file or directory).
 
```
 
chmod 2770 ~/directory

```

---

