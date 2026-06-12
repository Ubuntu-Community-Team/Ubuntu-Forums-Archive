---
title: "What Version Am I Running?"
date: 2010-03-26
forum: Desktop Environments
---

### Post by randell6564 on 2010-03-26
OMG..it's been a long time since I've been around the Ubuntu forums. Glad to be back.
I have two questions;

(1) What is the syntax for the command to see what version of Ubuntu is     running on this box?
It's been so long I've forgotten how to use the command line.

(2) Nobody knows the root password so we cant install anything or run updates. Cant I run as temporary root to accomplish these tasks; ie"sudo"?

Thanks!

---

### Post by new_tolinux on 2010-03-26
For what the version-question: no idea.

About sudo/root: there is no root-password, since Ubuntu has no working root account. Everything you want to do as root will need sudo from an account that has the privileges to run sudo.
When you want to do "a lot" as "root" try "sudo bash", type your user-password and then you will be root@localmachine. An "exit" will bring you back to user@localmachine status.
Edit: this is only for that terminal shell, not for the gui. Although you can use the terminal to start programs that are using the gui with root-privileges that way. So "nautilus" from a root-terminal will give you a root-privileged nautilus window for example.

---

### Post by sisco311 on 2010-03-26
> **randell6564 said:**
> 
(1) What is the syntax for the command to see what version of Ubuntu is     running on this box?

It's been so long I've forgotten how to use the command line.


```
lsb_release -a
```

> **randell6564 said:**
> 
(2) Nobody knows the root password so we cant install anything or run updates. Cant I run as temporary root to accomplish these tasks; ie"sudo"?


By default, the root account password is locked. You can to use sudo to run an application as root (it will prompt for your user password):
[uhelp]community/RootSudo[/uhelp]

---

### Post by macogw on 2010-03-26
1:  lsb_release -a
2: Yes, sudo is how things work around here.  Your user password is the password to enter when it asks.  And contrary to what the person above said,  you should *not* use "sudo" with graphical apps.  For those, use gksudo or kdesu.

---

### Post by new_tolinux on 2010-03-26
> **macogw said:**
> 2: Yes, sudo is how things work around here.  Your user password is the password to enter when it asks.  And contrary to what the person above said,  you should *not* use "sudo" with graphical apps.  For those, use gksudo or kdesu.

What's the difference? Never gave me any problem, at least not any I found.
To me gksudo is just 2 more characters to type.

Edit: this is a serious question.

---

### Post by coffeecat on 2010-03-26
> **new_tolinux said:**
> What's the difference? Never gave me any problem, at least not any I found.
To me gksudo is just 2 more characters to type.

Edit: this is a serious question.

And here's the serious answer.

Short answer:

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

More detailed answer:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by new_tolinux on 2010-03-26
Ok thanks for the information, now I understand why I never had any problems:
> **Why is it an issue?**
Well, to be perfectly honest, most of the time it isn't. For a lot of  applications, you can run them the improper way&#8212;using *sudo* for  graphical applications and see no adverse side effects.

I'll skip the rest, because that's far away from the OP's question.

---

### Post by randell6564 on 2010-03-26
> **sisco311 said:**
> ```
lsb_release -a
```



By default, the root account password is locked. You can to use sudo to run an application as root (it will prompt for your user password):
[uhelp]community/RootSudo[/uhelp]
Thank you sisco, and everyone but, what if you dont know the user password? As I said, the person who installed ubuntu on this box is not here and we cant run "sudo install-updates" or run updates from the package manager, OR install anything because I keep getting asked for a password.

---

### Post by wojox on 2010-03-26
Try and reset it: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by 2hot6ft2 on 2010-03-26
> **new_tolinux said:**
> What's the difference? Never gave me any problem, at least not any I found.
To me gksudo is just 2 more characters to type.

Edit: this is a serious question.
Then try gksu, there same number of letters...;)

---

### Post by sisco311 on 2010-03-26
> **2hot6ft2 said:**
> Then try gksu, there same number of letters...;)

gk<tab> = 3  

sud<tab> = 4

:evil:

---

### Post by randell6564 on 2010-03-26
> **wojox said:**
> Try and reset it: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Yeehaw...thank you wojox that worked! thanks to everyone.

---

