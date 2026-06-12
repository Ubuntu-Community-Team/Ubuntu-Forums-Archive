---
title: "[SOLVED] Accessing files"
date: 2008-12-08
forum: General Help
---

### Post by gandalf458 on 2008-12-08
I'm really confused. I'm using Apache with my files in var/www. From time to time I copy some files from a USB stick to var/www but when I try to access some of the files in Apache I get a 403 forbidden error. I also have a problem that not all files get copied across - presumably because of ownership and/or permissions.

I know chown is for changing owner and chmod for changing permissions but what owner and permissions I should set www and its contents to so I don't have these two problems in future.

Can anyone help please?

---

### Post by p_quarles on 2008-12-08
Well, generally speaking the easiest way to ensure that Apache can read a file is to make the file world-readable:
```
sudo chmod a+r /path/to/file
```
To do the same to the directory:
```
sudo chmod -R a+r /var/www
```
Note that this is the easiest way, and not necessarily the recommended way for a public site hosting complex server side scripting or database manipulation. With those factors, you may need things more locked down than that, but for static web pages world-readable is likely to be fine.

---

### Post by gandalf458 on 2008-12-08
Thanks. It's not a public site so I don't have problems in that department. But I'm afraid I'm being dim. Does
```
sudo chmod -R a+r /var/www
```
only change the directory permissions or does it change all sub-directories and their contents?

---

### Post by Idefix82 on 2008-12-08
With the -R option it changes the directory permission as well as that of its content (including subdirectories and their content). Without the -R option it would just change the permissions for the directory.

---

### Post by gandalf458 on 2008-12-08
Thanks. I realised that all I had to do was try it and see!

Cheers guys. :)

---

### Post by gandalf458 on 2008-12-08
One thing, having done 
```
sudo chmod -R a+r /var/www
```
some of my sub-directories are still shown with a padlock. What am I missing now please?

---

