---
title: "/etc/apt-sources.list missing (Solved)"
date: 2005-12-02
forum: Desktop Environments
---

### Post by dw5437 on 2005-12-02
I went to the enabling extra repositories site and followed the instructions for enabling universe and multiverse repositories and I lost the entire list. When I open kwrite I see the list but I get an error message when I open Kwrite in a console as follows:

dw5437@ubuntu1:~$ sudo kwrite /etc/apt/sources.list
Error: "/var/tmp/kdecache-dw5437" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-dw5437" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
dw5437@ubuntu1:~$

Anybody have any ideas? Now Adept won't even open. Any help much appreciated.

---

### Post by ubuntu_demon on 2005-12-02
you can try to do it in the terminal :
$sudo pico /etc/apt/sources.list

if it fails we are going to check the permissions. Please give us the results of the following commands :

$lsattr /etc/apt/sources.list 

$ls -al /etc/apt/sources.list

---

### Post by dw5437 on 2005-12-02
dw5437@ubuntu1:~$ lsattr/etc/apt/sources.list
bash: lsattr/etc/apt/sources.list: No such file or directory
dw5437@ubuntu1:~$ ls - al /etc/apt/sources.list
ls: -: No such file or directory
ls: al: No such file or directory
/etc/apt/sources.list
dw5437@ubuntu1:~$

The 1st command you gave me pulls up the list, but it is missing some entries. Don,t know how to edit from that list.
Thanks for the reply.

---

### Post by GeneralZod on 2005-12-02
I think there were a few typos in Ubuntu_Demon's post.

Try

```

ls -al /etc/apt/sources.list

```

(no space between "-" and "a"!).

Also, try

```

kdesu kwrite /etc/apt/sources.list

```

---

### Post by ubuntu_demon on 2005-12-02
yeah some stupid typos :-P
I fixed them.

---

### Post by dw5437 on 2005-12-02
Thanks guys. I got knocked off of the internet all day and just now got to your posts. Will give these a shot and post results.

---

### Post by dw5437 on 2005-12-02
Okay, tried that and this is what I got

-rw-r--r--  1 root root 1551 2005-12-02 04:40 /etc/apt/sources.list

---

### Post by dw5437 on 2005-12-03
Well I don't know what happened but I edited it in Kwrite again and it finally worked. I appreciate the help very much. A good day to all

---

