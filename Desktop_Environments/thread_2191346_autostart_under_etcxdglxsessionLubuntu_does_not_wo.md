---
title: "autostart under /etc/xdg/lxsession/Lubuntu/ does not works"
date: 2013-12-02
forum: Desktop Environments
---

### Post by martro on 2013-12-02
Hi,
i don't know if is a bug.
I'm trying to start a script after login.
My script is that:

```
#!/bin/bash

echo "Hello World" > /tmp/hello.txt
```

if i running it from shell

```
./hello.sh 
user@localhost:~/Desktop$ ls -alh /tmp/hello.txt 
-rw-rw-r-- 1 user user 12 dic  2 11:12 /tmp/hello.txt
```

Well. I'm changing /etc/xdg/lxsession/Lubuntu/autostart like this

```
@/home/user/Desktop/hello.sh

```

but after login nothing happens

```
ls -alh /tmp/hello.txt
ls: cannot access /tmp/hello.txt: No such file or directory

```

but if i'm changing local autostart

```
cat /etc/xdg/lxsession/Lubuntu/autostart > /home/user/.config/lxsession/Lubuntu/autostart

```

after login it works

```
ls -alh /tmp/hello.txt 
-rw-r--r-- 1 user user 12 dic  2 11:44 /tmp/hello.txt

```

What's wrong? How can set my lubuntu in order to run the same script for all users?

---

