---
title: "Eternal Lands Help"
date: 2006-09-18
forum: Gaming &amp; Leisure
---

### Post by cac007 on 2006-09-18
ok here are the instructions to install:
To play on Linux:
Download the zip file, and unzip it.
cd to the directory where you installed it.
chmod to 775 and execute el.x86.linux.bin
edit el.ini and change datadir to where you unzip everything
Also, the zip file has no base directory, so you should unzip it in a new directory you create.
To play under FreeBSD, download the Linux version, download the code from the CVS, and use the freebsd make file.

i have unziped the file.  i used chmod -x el.x86.linux.bin.  and i get the following error:  
[email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ sudo ./el-132.x86.linux.bin
Password:
sudo: ./el-132.x86.linux.bin: command not found

what am i doing wrong

---

### Post by Carbon Based on 2006-09-19
Try typing ```
sudo bash el-132.x86.linux.bin
```
That should work

---

### Post by cac007 on 2006-09-19
[email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ sudo bash el-132.x86.linux.bin
Password:
el-132.x86.linux.bin: el-132.x86.linux.bin: cannot execute binary file

---

### Post by Carbon Based on 2006-09-19
Ok, alternate method:
```
cory@ubuntu:~/Desktop/el_132_linux_full.zip_FILES$ sudo -i
```
Enter your password and a root shell should come up:
```
root@ubuntu:~/root$ ./el-132.x86.linux.bin
```

EDIT: Actually I think your problem is this: to make files executable, type ```
chmod +x file
``` rather than chmod -x file. Then execute it with either of my methods and it should work.

---

### Post by cac007 on 2006-09-19
[email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ sudo -i
Password:
root@ubuntu:~# ./el-132.x86.linux.bin
-bash: ./el-132.x86.linux.bin: No such file or directory


[email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ chmod +x [email]el-132.x86.linux.bincory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ ./el-132.x86.linux.bin
./el-132.x86.linux.bin: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by cac007 on 2006-09-19
> **cac007 said:**
> [email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ sudo -i
Password:
root@ubuntu:~# ./el-132.x86.linux.bin
-bash: ./el-132.x86.linux.bin: No such file or directory


[email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ chmod +x [email]el-132.x86.linux.bincory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ ./el-132.x86.linux.bin
./el-132.x86.linux.bin: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory


should i just give up?

---

### Post by jISh on 2006-09-19
You can't execute it because you still didn't give it permissions.
You don't need the ./ when you are passing the filename to a command. 
So *chmod 775 el-132.x86.linux.bin* should work.

When you want to execute it, use the ./

Edit: And don't use sudo to launch it. sudo is dangerous and should not be used when not needed. That'll give you permission. 

As far as your dependancy problem, there's a post somewhere on these forums that will explain which you need. In fact, a search would have yielded you all the answers to questions asked here.

---

### Post by cac007 on 2006-09-19
[email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ chmod 775 el-132.x86.linux.bin
[email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ ./el-132.x86.linux.bin
./el-132.x86.linux.bin: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by IAmNotPhillip on 2006-09-19
sudo apt-get install lib-sdl1.2 libopenal0 libcal3d11c2a

---

### Post by Carbon Based on 2006-09-19
> **cac007 said:**
> [email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ sudo -i
Password:
root@ubuntu:~# ./el-132.x86.linux.bin
-bash: ./el-132.x86.linux.bin: No such file or directory


[email]cory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ chmod +x [email]el-132.x86.linux.bincory@ubuntu:~/Desktop/el_132_linux_full.zip[/email]_FILES$ ./el-132.x86.linux.bin
./el-132.x86.linux.bin: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory
You have to cd to the directory the file is in. sudo -i acts like opening a new terminal window, so you'd have to 
```
cd /home/cory/Desktop/el_132_linux_full.zip_FILES

./el-132.x86.linux.bin
```

And as IAmNotPhillip said, you will probably have to install those packages.

---

