---
title: "yum update problem.Help needed quick.!  o_0"
date: 2008-03-07
forum: Fedora/RedHat and derivatives
---

### Post by poisonblack on 2008-03-07
Hullo,

I installed Fedora 8 on my PC a few days ago, but haven't yet suceeded in getting yum to work for me.Whenever I try installing any application, I get this:
```
[root@localhost yum.repos.d]# yum install k3b
http://devel.foss.org.my/%7Ekagesenshi/repo/pub//repodata/repomd.xml: [Errno 14] HTTP Error 404: Not Found
Trying other mirror.
Error: Cannot retrieve repository metadata (repomd.xml) for repository: kagesenshi. Please verify its path and try again
[root@localhost yum.repos.d]#
```
I have kagesenshi and Livna repos enabled.But I can't seem to find a fix for this error.Any help.?

---

### Post by RebounD11 on 2008-03-07
Is your network setup correct? I got that problem when I didn't setup my proxy server correctly.

---

### Post by igknighted on 2008-03-07
I don't think Kagasenshi's repo works anymore.  What do you need from there?

---

### Post by RebounD11 on 2008-03-08
> **poisonblack said:**
> Hullo,

I installed Fedora 8 on my PC a few days ago, but haven't yet suceeded in getting yum to work for me.Whenever I try installing any application, I get this:
```
[root@localhost yum.repos.d]# yum install k3b
http://devel.foss.org.my/%7**[COLOR="DarkRed"]/[/COLOR]**Ekagesenshi/repo/pub//repodata/repomd.xml: [Errno 14] HTTP Error 404: Not Found
Trying other mirror.
Error: Cannot retrieve repository metadata (repomd.xml) for repository: kagesenshi. Please verify its path and try again
[root@localhost yum.repos.d]#
```
I have kagesenshi and Livna repos enabled.But I can't seem to find a fix for this error.Any help.?

I just spotted sth that coul be wrong in your repo web address... I put in red what I think is wrong...

besides you are using the fedora 7 repo...

---

### Post by poisonblack on 2008-03-08
Removing kagesenshi repos did the trick.Thanks.!

---

