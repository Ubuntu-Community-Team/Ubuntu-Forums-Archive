---
title: "sudo and '&gt;&gt;' hate eachother"
date: 2006-09-12
forum: Desktop Environments
---

### Post by navilon on 2006-09-12
why does this work:
```
su root
root# echo "this will be a line in a file" >> /etc/newfile
```

but this doesn't
```
sudo echo "this will be a line in a file" >> /etc/newfile
```

](*,)

---

### Post by Ramses de Norre on 2006-09-12
Because redirecting (>>) is a shell in built and not a command, in your first example the shell is ran by root and thus the redirecting is ran by root and has appropriate permissions.

In the second example though the shell is ran by your regular user and only the program echo has root permissions, not the redirecting.

A way to work around this is using a program instead of the shell in built, and this program is tee in this case, so instead of ```
sudo echo "this will be a line in a file" >> /etc/newfile
```
You need to do ```
echo "this will be a line in a file"|sudo tee -a /etc/newfile
```
The -a is to make tee append the line to the file (like >> does), without this option tee will overwrite the file (like > does).

---

### Post by kaamos on 2006-09-12
```
sudo su -c 'echo "this will be a line in a file" >> /etc/newfile'
```
works as well.

---

