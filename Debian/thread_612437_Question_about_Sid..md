---
title: "Question about Sid."
date: 2007-11-13
forum: Debian
---

### Post by mivo on 2007-11-13
How "unstable" is Sid? I known it is unstable in theory, but how common/bad are the problems that you are likely to encounter if you use these repositories? Also, if you do use Sid, do you essentially have a "rolling release" distro that requires no "version updates"?

---

### Post by kerry_s on 2007-11-13
i use lenny/sid with no problems. you just got to read and understand what is going to be updated, don't force anything and check carefully when it wants to remove stuff.

using sid you run the latest, no rolling release just update at your leisure, i'll usually check once a week.

if your starting from etch you need to go lenny first, then sid.

here's what i use->

```

deb http://www.debian-multimedia.org sid main
deb http://ftp.debian.org/debian/ lenny main non-free contrib 
deb http://ftp.debian.org/debian/ sid main non-free contrib 
deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 


```

---

### Post by markharding557 on 2007-11-14
> **mivo said:**
> How "unstable" is Sid? I known it is unstable in theory, but how common/bad are the problems that you are likely to encounter if you use these repositories? Also, if you do use Sid, do you essentially have a "rolling release" distro that requires no "version updates"?
unstable means things can be buggy and maybe not work correctly.
eg a while ago synaptic was not working in sid

---

### Post by -grubby on 2007-11-14
there is no "sid" It's just lenny with the unstable repositories (unstable,duh!)

---

### Post by Antman on 2007-11-14
Just run Sidux.... they try to make Sid as "stable" as possible....
See my sig.:guitar:

---

### Post by b9anders on 2007-11-15
> **nathangrubb said:**
> there is no "sid" It's just lenny with the unstable repositories (unstable,duh!)

That doesn't make any sense. If you relying on the packages from the unstable repositories, you are using debian unstable, not testing.

---

### Post by markharding557 on 2007-11-15
> **nathangrubb said:**
> there is no "sid" It's just lenny with the unstable repositories (unstable,duh!)

see this link[http://www.debian.org/releases/unstable/]("http://www.debian.org/releases/unstable/")

---

