---
title: "Installing Proe Wildfire 2 In Ubuntu 7.04 Feisty Fawn, Procedure need to properly ins"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by cyanide on 2007-06-19
Hi everyone,

I use Ubuntu feisty fawn as my main OS. I have been trying for the past year to install Proe Wildfire 2 on it with varying degrees of success. I am hoping some one in this forum will guide me through the install properly.

In the previous version of Ubuntu ie Ubuntu 6.10 Edgy Eft, I was able to run the installation script. However,ever time I tried to run the Proe script ,I got the error message "setenv: too many variables"

In the latest version of Ubuntu,ie Ubuntu 7.04 Fesity Fawn, I am not even able to run the installation script. I get the error " bash:shell not found".

These are the pages I followed to install proe,

[http://forum.ubuntu.org.cn/viewtopic.php?t=3425](http://forum.ubuntu.org.cn/viewtopic.php?t=3425)
[http://blogs.ittoolbox.com/linux/locutus/a...der-linux-12695](http://blogs.ittoolbox.com/linux/locutus/a...der-linux-12695)

Proe Wildfire is essential for my research.

Any help is greatly appreciated.

Regards

---

### Post by neptho on 2007-06-19
Try fixing your path:
```
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:$PATH;export PATH
```

If that still doesn't work, try 
```
/bin/bash <install script>
```

If that fails:

```
%dpkg -s bash | awk '/Status/ { print $4 }'
```

It should say 'installed'.  If it does not, you've got a bigger problem.

If it does say 'installed', and still doesn't work, finally, try:

```
%sudo dpkg-reconfigure dash
```

..and tell it 'No' to use bash instead of dash.

---

### Post by cyanide on 2007-06-21
Hi,
    Initially I had the problem while trying to run the Proe installation script I got the error " bash:shell not found".
Now when I try to run the script it says "setup not found". When I type "ls" command I can see the installation script. can anyone tell me cause of this problem.

Any help is appreciated.
 
Thankyou.

---

### Post by neptho on 2007-06-21
Uhm.. try posting the return of an 'ls -l' in the directory with the setup files.

---

### Post by cyanide on 2007-06-21
This is the result  of the command,

> 
cyanide@cyanide-laptop:~/pro$ ls -l
total 40
drwxr-xr-x 2 cyanide cyanide 4096 2007-06-19 21:11 crack
drwxr-xr-x 5 cyanide cyanide 4096 2007-06-19 21:11 dsrc
-rw-r--r-- 1 cyanide cyanide 3556 2007-06-19 21:11 getpmt.csh
drwxr-xr-x 4 cyanide cyanide 4096 2007-06-19 21:11 html
-rw-r--r-- 1 cyanide cyanide 2631 2007-06-19 21:11 ProE_Linux_setup.txt
drwxr-xr-x 2 cyanide cyanide 4096 2007-06-19 21:11 ptc_inst
drwxr-xr-x 2 cyanide cyanide 4096 2007-06-19 21:12 ptcsh0
-rw-r--r-- 1 cyanide cyanide 6940 2007-06-19 21:11 setup
drwxr-xr-x 3 cyanide cyanide 4096 2007-06-19 21:12 uninstall


I am not sure,but can this problem be related to beryl???

This is what I get when i try to run the setup file,

> 
cyanide@cyanide-laptop:~/pro$ sudo ./setup
Password:
sudo: ./setup: command not found



> 
cyanide@cyanide-laptop:~/pro$ sudo -s
root@cyanide-laptop:~/pro# sudo ./setup
sudo: ./setup: command not found



Any help is appreciated.

---

