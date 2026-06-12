---
title: "sudo - how does it work???"
date: 2005-08-04
forum: Desktop Environments
---

### Post by daller on 2005-08-04
Hi All,

I don't understand the "sudo"-command

You can make the superuser run "apt-get update", but not something like "echo "deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main" >> /etc/apt/sources.list"! Why???

I am trying to make a shellscript that should create a superuser password, if that is not already done... How do I do that? - any suggestions?

---

### Post by dave9191 on 2005-08-04
The sudo command alows you to run commands as if the root user run them. So if you have a command you wish to execute as the root user you simply put sudo before it and enter your password. If you need to set the root password you can "sudo passwd". And if you need a root console "sudo bash" works fine :)

If you need more info, then there are things in the wiki and online about it. 

Dave

---

### Post by daller on 2005-08-04
Well, sudo -l tells me:

User daniel may run the following commands on this host:
    (ALL) ALL

sudo -e echo "deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main" >> /etc/apt/sources.list

Permission denied!

---

### Post by cwaldbieser on 2005-08-04
I am not sure why file redirection doesn't work under sudo-- maybe because sudo empowers the *command* you give and not other aspects of the shell.  In any event, you could just do

```
$ sudo sh -c "echo "deb http://kubuntu.org/hoary-kde342 hoary-updates main" >> /etc/apt/sources.list"
```

This creates an empowered subshell to do the heavy lifting.

---

### Post by daller on 2005-08-04
This is really weird:

daniel@ubuntu:~$ sudo sh -c "echo "deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main" > /etc/apt/sources.list"
deb

It outputs "deb" - can't figure out why!

---

### Post by daller on 2005-08-04
...same thing in all my commands...

...seems like "sh" doesn't like spaces

---

### Post by dave9191 on 2005-08-04
Err... just a note on that command. 

sudo sh -c "echo "deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main" >> /etc/apt/sources.list"

You open the " before the echo and close it after the space before the deb. You need to escape the quotes inside with a \

sudo sh -c "echo \"deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main\" >> /etc/apt/sources.list"

Or just sudo bash and run that command in there. 

Dave

---

