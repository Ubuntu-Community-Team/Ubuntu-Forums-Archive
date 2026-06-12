---
title: "trouble with copying files to /usr/bin"
date: 2009-03-31
forum: General Help
---

### Post by quackhacker44 on 2009-03-31
im trying to copy a file to /usr/bin ```
sudo cp /home/user/Desktop/0.20/dockbar.py /usr/bin
``` i keep getting a error "cannot stat '/.../dockbar.py' no such file or directory." Am i just incredibly stupid or is there another reason why its not working?

---

### Post by adult swim on 2009-03-31
do you have the correct path to the file?

---

### Post by stderr on 2009-03-31
Are you sure your username is 'user'?

/home/username/...

---

### Post by lloyd_b on 2009-03-31
> **quackhacker44 said:**
> im trying to copy a file to /usr/bin ```
sudo cp /home/user/Desktop/0.20/dockbar.py /usr/bin
``` i keep getting a error "cannot stat '/.../dockbar.py' no such file or directory." Am i just incredibly stupid or is there another reason why its not working?

At a guess, I'd say you have a problem with the path you're giving for that file.  Try this:```
cd ~/Desktop
cd 0.20
ls
```This will verify that the path is valid, and let you see that there is in fact a "dockbar.py" in that directory.

A comment - I recommend against putting anything in "/usr/bin" unless you absolutely have to.  In this case, you should be able to create a "~/bin" directory, and copy the file there, and have that script accessible just as if it was in "/usr/bin".  The only reason for putting it in "/usr/bin" would be if you want it to be accessible to multiple users on the machine...

Lloyd B.

---

### Post by quackhacker44 on 2009-03-31
thanks a bunch that made it work :)

---

