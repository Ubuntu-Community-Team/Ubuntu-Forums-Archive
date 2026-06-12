---
title: "use chown to change files but not folders"
date: 2009-05-19
forum: General Help
---

### Post by RedWagon on 2009-05-19
I used to have all my files on an NTFS drive but recently moved everything over to EXT3 (I don't even dual boot for games any more.)  Everything worked fine, the only problem is that all my files are -rwxr-xr-x due to the way the NTFS drive was mounted.  I can change the files in a directory by 
sudo chown 644 * 
but when I try to do 
sudo chown -R 644 *
it changes the directories also which prevents them from opening.  Luckily I thought this might be an issue and didn't do the whole drive so right now all my files are still -rwxr-xr-x and directories are drwxr-xr-x.
 
My question is how do I change the ownership of all the files on this drive without chagning the permissions of the directories themselves?

---

### Post by snova on 2009-05-19
Combine it with find:

```
find -type f -exec sudo chmod 644 {} \;
```

---

### Post by RedWagon on 2009-05-19
perfect, but before I run this what does the {} and \; do?  I use command line a lot and I like to know exactly what's happening with every command.

---

### Post by geirha on 2009-05-19
-exec will run a command for each matching file. {} is the place-holder for the file, and \; means the command ends here. It is explained in find's manual page. ```
man find
```

You can also use xargs to achieve the same
```
find -type f -print0 | xargs -0 chmod 644 --
```

---

### Post by adult swim on 2009-05-19
im pretty sure, and someone correct me if im wrong, that the find command will locate your individual files and pass them the the command sudo chmod 644 .  the {} is a placeholder for the information taht the find command returns, in essence will pass each file name through to the chmod 644.  the \; is convention for the end of the -exec command.
edit: too slow for geihra

---

### Post by asmoore82 on 2009-05-19
see the capital X permission in `chmod` ...
[quote="man chmod"]execute/search only  if  the file is a directory or already has execute permission for some user (X)[/quote]

you could use something in the form of
```
sudo chmod -R -rwx *target_folder*
sudo chmod -R u+rwX,go+rX *target_folder*
```

OR, I like the readability of this much better:

```
sudo chmod -R -rwx *target_folder*
sudo chmod -R +rX *target_folder*
sudo chmod -R u+w *target_folder*
```

---

### Post by RedWagon on 2009-05-20
makes sense, and snova's command worked perfectly.  Thanks everyone!

---

