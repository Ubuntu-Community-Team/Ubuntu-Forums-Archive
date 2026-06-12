---
title: "No root?"
date: 2009-01-07
forum: General Help
---

### Post by igor056 on 2009-01-07
ubuntu 8.10
Can someone please tell me why they seem to have done away with the root user on this Linux issue.  Yes I know I can use the sudo thing but this gets old very quickly.  I know there must be a reason for it, I just cannot see it.  Surely it is not to make it more 'Windows' like? Heaven forbid.
The install won't let you select root as your installation user.
I have even tried adding root, post install but it won't have that either, just says that it is reserved for administration.
So other than the installer, who would get to use it?

---

### Post by jespdj on 2009-01-07
Why would sudo "get old quickly" and what would be the advantage of enabling the root user over sudo? If you have to type multiple commands and don't want to type "sudo" in front of each command, then type:
```
sudo -i
```
to get into a shell with root privileges.

> **igor056 said:**
> The install won't let you select root as your installation user.
Because it is very unsafe and absolutely unnecessary to do everything as root. Doing this would defeat the whole security system. You do not need the root account.

Read this if you want to know more about why Ubuntu works with sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Note that there's a [forum policy](http://ubuntuforums.org/showthread.php?t=716201) which forbids posting tutorials on how to enable the root account.

---

### Post by exploder on 2009-01-07
The reason there is no actual root account makes sense when you think about it. A typical Windows user is always logged on as administrator, the whole system is wide open for attacks and usually is cause for repeated reinstalls of the operating system.

By using sudo the system is not left wide open and the chance of attack is very slim. Is it really that inconvenient to type four letters a command and your password? Using sudo keeps your important data secured and you system safe. There are very rare instances where an administrator might need actual root access to the system for specialised tasks but an administrator would already have the knowledge to do so.

It is best to use sudo and the policy on this forum is for good reason.Using sudo forces you to learn new habits and they are good ones!

---

### Post by adamlau on 2009-01-07
I see it the other way around. Instead of commenting in and adding myself to the wheel group, Ubuntu already did the work for me upon install :) .  

```
gksu gdmsetup
```

The root account is there is you want to log in to it. Security > Allow local system administrator login

---

### Post by igor056 on 2009-01-17
Thanks for all the replies.  Guess I am now getting used to the new flavor and can now see the point to it all.
Whatever it is always going to beat the MS crowd.

---

