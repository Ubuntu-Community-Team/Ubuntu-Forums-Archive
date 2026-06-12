---
title: "deb problems using alien"
date: 2009-07-20
forum: Desktop Environments
---

### Post by andrea000 on 2009-07-20
I converted a rpm to a deb using sudo alien it converted
fine but now when i go to get the deb there is a pad lock
icon above it and when i do a properties and permissions
it will not let me change them at the bottom it also says
you are not the owner so you cant change these is there
any way i can change them?

---

### Post by bryonak on 2009-07-20
If it required "sudo", then the created package belongs to the root user.

If you are comfortable with the terminal, this problem can be solved quickly by installing the package anyway with```
sudo dpkg -i PATH_TO_PACKAGE
```


If you prefer a GUI to change the permissions, press Alt+F2 and type```
gksudo nautilus
```This will start your file manager in administrator (root) mode. Browse to the package and right click on it. After choosing Properies -> Permissions you should be able to change them.

You can also change the owner via terminal:```
sudo chown YOURNAME FILENAME
```

---

### Post by andrea000 on 2009-07-20
Thank you i had already tried sudo nautilus
but the other command line way worked really
good thank you so much

---

