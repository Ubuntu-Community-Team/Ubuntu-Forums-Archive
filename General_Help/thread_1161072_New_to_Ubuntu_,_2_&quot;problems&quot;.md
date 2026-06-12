---
title: "New to Ubuntu , 2 &quot;problems&quot;"
date: 2009-05-16
forum: General Help
---

### Post by MaRiOsGR on 2009-05-16
Hello,

I'm totaly new to ubuntu and I just istalled it on my Laptop.
I used the 9.04 i386 DVD iso .

there are 2 things that I would like to "fix"

1. How can I install KDE? I see that only Gnome is available in my sessions.

2.at the shell console I try to be root and I cant...(using the command su and then give my password).
at the installation of ubuntu the setup never asked me to give the root password, only my user's pass , I know that I can run command with the "sudo" but I would like to know how I can be root.

thank you.

---

### Post by MaRiOsGR on 2009-05-16
it seems that " sudo apt-get install kubuntu-desktop "
did the trick (i'll now for sure after the installation finishes).

now only the thing with the root user remains :)

---

### Post by Moe The Cat on 2009-05-16
> **MaRiOsGR said:**
> 1. How can I install KDE? I see that only Gnome is available in my sessions.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Zalbor on 2009-05-16
You can go to a "permanent" root shell with the command "sudo -s". :)

---

### Post by MaRiOsGR on 2009-05-16
> **Moe The Cat said:**
> [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

I did use this article but it couldnt find any package "kubuntu" at all.

but thats ok apt-get gave me the solution :)

---

### Post by MaRiOsGR on 2009-05-16
> **Zalbor said:**
> You can go to a "permanent" root shell with the command "sudo -s". :)

that works thank you :)

---

### Post by leandromartinez98 on 2009-05-16
> **Zalbor said:**
> You can go to a "permanent" root shell with the command "sudo -s". :)

I prefer "sudo su"

because the prompt becomes the "root" prompt, with the usual "#"

---

### Post by Cheesemill on 2009-05-16
Check out these links for why the root account is disabled in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1161056](http://ubuntuforums.org/showthread.php?t=1161056)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Cheesemill

---

### Post by Zalbor on 2009-05-17
> **leandromartinez98 said:**
> I prefer "sudo su"

because the prompt becomes the "root" prompt, with the usual "#"
It does with -s too.

---

### Post by leandromartinez98 on 2009-05-18
> **Zalbor said:**
> It does with -s too.

Not for me:

leandro@xxxx:~% sudo -s
root@xxxx:~% 

leandro@xxxx:~% sudo su
root@xxxx:/home/leandro#

Nothing really relevant, anyway.

---

### Post by baseface on 2009-05-18
```
sudo passwd root
```
then u can su to root.

---

### Post by helofromseattle on 2009-05-18
or if you want a full root session just go to Login Window preferences then security click allow system administrator login, then set a password for root in users and groups. Now you should be able to login as root. Hope this helps:p

---

### Post by Zalbor on 2009-05-19
> **leandromartinez98 said:**
> Not for me:

leandro@xxxx:~% sudo -s
root@xxxx:~% 

leandro@xxxx:~% sudo su
root@xxxx:/home/leandro#

Nothing really relevant, anyway.
Strange, that's how it is for me:
```
user@user-laptop:~$ sudo -s
[sudo] password for user:
root@user-laptop:~# exit
exit
user@user-laptop:~$ sudo su
root@user-laptop:/home/user#
```
The only difference is that with "su" I remain at the directory I was.

I've never seen a % prompt though...

---

### Post by leandromartinez98 on 2009-05-20
> **Zalbor said:**
> Strange, that's how it is for me:
```
user@user-laptop:~$ sudo -s
[sudo] password for user:
root@user-laptop:~# exit
exit
user@user-laptop:~$ sudo su
root@user-laptop:/home/user#
```
The only difference is that with "su" I remain at the directory I was.

I've never seen a % prompt though...

The % is my user-specified prompt (in my .bashrc file), which
I think is being read when using "sudo -s", also when using "sudo bash". But the most important difference is that with "sudo -s" the "home" directory continues to be the user home, while using "sudo su" the home directory turns to be the root home directory.

---

