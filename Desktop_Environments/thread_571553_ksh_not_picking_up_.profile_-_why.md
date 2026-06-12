---
title: "ksh not picking up .profile - why?"
date: 2007-10-09
forum: Desktop Environments
---

### Post by david68 on 2007-10-09
Hi all,

I have no idea why this is happening and have looked in the forum with no luck.

I am using ksh on Ubuntu 6.06.   Reason being this is what we use at work (so bash NOT an option for me)

I've configured my account to use ksh from the Users/Groups program and checked that when I launch GNOME terminal, I am definitely using ksh not bash (used ps).

My problem is that although I've created a .profile file in my home dir (/home/david/), ksh is not reading it.  I 've an alias which it's ignoring, and the prompt is also being ignored.

The contents of the file are:
PATH=/home/david
export PATH

prompt='$PWD:'
alias h='history'

Does anyone know what I've done wrong?  Any help would be appreciated.

thx

David

---

### Post by mali2297 on 2007-12-30
The problem is that gdm does not read ~/.profile. Try the solution posted here:
[http://ubuntuforums.org/showpost.php?p=2876782&postcount=8](http://ubuntuforums.org/showpost.php?p=2876782&postcount=8)

That is, add the line
```

. ~/.profile

```
to the file /etc/profile.

---

