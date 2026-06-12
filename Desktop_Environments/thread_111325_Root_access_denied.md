---
title: "Root access denied?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by r4ik on 2006-01-02
There must be a simple way around this but i cant find it.
Some help would be nice .
Thanks.
Here's my output,

r4ik@ubuntu:~$ sudo -i
root@ubuntu:~# /etc/apt/sources.list
-bash: /etc/apt/sources.list: Permission denied
root@ubuntu:~# sudo su
root@ubuntu:~# /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
root@ubuntu:~#

Could be i am overlooking the obvious only human.

---

### Post by ardchoille on 2006-01-02
[QUOTE=r4ik]There must be a simple way around this but i cant find it.
Some help would be nice .
Thanks.
Here's my output,

r4ik@ubuntu:~$ sudo -i
root@ubuntu:~# /etc/apt/sources.list
-bash: /etc/apt/sources.list: Permission denied
root@ubuntu:~# sudo su
root@ubuntu:~# /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
root@ubuntu:~#

Could be i am overlooking the obvious only human.[/QUOTE]
What are the permissions on /etc/apt/sources.list? Open a term and type"
```

ls -l /etc/apt/sources.list

```
Post the output if you'd like.

---

### Post by r4ik on 2006-01-02
Here is the output,

r4ik@ubuntu:~$ ls -l /etc/apt/sources.list
-rw-r--r--  1 root root 2456 2006-01-02 00:07 /etc/apt/sources.list
r4ik@ubuntu:~$

Does not tell me much....

---

### Post by Pablo_Escobar on 2006-01-02
You are trying to execute a command with 
> **/etc/apt/sources.list**

You need to put something in front if You want to edit it, because it's only a text file.
Try :
> sudo gedit /etc/apt/sources.list
(Gnome)

> sudo kate /etc/apt/sources.list
(KDE)

Info : Gedit is a text editor for Gnome while kate is a text editor for KDE. Sudo gives You root powers to edit outside /home folder.

---

### Post by r4ik on 2006-01-02
[QUOTE=Pablo_Escobar]You are trying to execute a command with 


You need to put something in front if You want to edit it, because it's only a text file.
Try :

(Gnome)


(KDE)[/QUOTE]


sudo gedit /etc/apt/sources.list
It got me my list thanks a lot !

---

### Post by Desiree on 2007-09-25
> **Pablo_Escobar said:**
> sudo gedit /etc/apt/sources.list
This worked for me too!  Thanks Pablo!
:guitar:

---

### Post by Rupertronco on 2007-09-26
If you're newer to APT/Ubuntu, I'd suggest using the GUI way of editing your sources.list file. 

That can be found through System>Administration>Software Sources

---

### Post by Rupertronco on 2007-09-26
How are you trying to install it? Through synaptic or did you download a .deb file or a tar.gz file?

---

### Post by Desiree on 2007-10-01
I actually managed to mess up the GUI method prior to editing source.list directly, which I was able to follow the instructions to easily enough.  Haven't spent too much time on the GUI, but I'm not sure how I would have achieved the same result that way yet.

---

### Post by idkwot on 2007-10-01
same thing happened to me

---

