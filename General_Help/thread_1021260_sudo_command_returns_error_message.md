---
title: "sudo command returns error message"
date: 2008-12-25
forum: General Help
---

### Post by nithuldershs on 2008-12-25
Plz help me ,I am a beginner
My problem is when I type sudo command in Terminal
I'm getting an error message

"host name<host name> cannot be resolved."

Plz tell me how can I solve this problem.
This error first occurred when I tried to configure
my internet connection using command "sudo pppoeconfig"

---

### Post by mick222 on 2008-12-25
ifconfig is the command youu should have used no need for sudo
whats the problem with your internet.

---

### Post by obsrv on 2008-12-25
You can add you *hostname* to /etc/hosts file, so it will be resolvable

Add line like this:

```
127.0.0.1 <hostname>
```

---

### Post by caljohnsmith on 2008-12-25
Often that "unresolved host name" type error when using sudo means that your computer's hostname is slightly different between the /etc/hosts and /etc/hostname files. How about posting the output of the following:
```
cat /etc/hosts
cat /etc/hostname
```

---

### Post by nithuldershs on 2008-12-27
> **caljohnsmith said:**
> Often that "unresolved host name" type error when using sudo means that your computer's hostname is slightly different between the /etc/hosts and /etc/hostname files. How about posting the output of the following:
```
cat /etc/hosts
cat /etc/hostname
```

I got the following response in terminal
Is there any problem in this?

```
nit@nithul-desktop:~$ cat /etc/hosts

127.0.0.1 localhost

127.0.1.1 nithul-desktop.nithul-desktop


# The following lines are desirable for IPv6 capable hosts

nit@nithul-desktop:~$ cat /etc/hostname

nithul-desktop
```

---

### Post by caljohnsmith on 2008-12-27
> **nithuldershs said:**
> I got the following response in terminal
Is there any problem in this?

```
nit@nithul-desktop:~$ cat /etc/hosts

127.0.0.1 localhost

127.0.1.1 [COLOR="Blue"]nithul-desktop.nithul-desktop
[/COLOR]

# The following lines are desirable for IPv6 capable hosts

nit@nithul-desktop:~$ cat /etc/hostname

[COLOR="Blue"]nithul-desktop[/COLOR]
```
Unfortunately, yes, that is a problem; the names have to exactly match. To fix it, you could either boot into "recovery mode", or you could mount your Ubuntu partition from the Live CD. If you boot into recovery mode, you could do:
```
nano /etc/hosts
```
And then change "nithul-desktop.nithul-desktop" to just "nithul-desktop". Save the file by pressing Ctrl-X, say "y" to save the change, reboot, and you should be OK using sudo again. Let me know how it goes or if you run into problems.

---

### Post by nithuldershs on 2008-12-28
Thank you Mr.Caljohnsmith that helped me solve my problem

---

### Post by caljohnsmith on 2008-12-28
You're welcome, and glad to hear that fixed the problem. Cheers and have fun with Ubuntu. :)

---

