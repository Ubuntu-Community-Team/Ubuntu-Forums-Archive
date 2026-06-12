---
title: "useradd/passwd don't seem to work"
date: 2006-08-18
forum: Desktop Environments
---

### Post by ifishfortorque on 2006-08-18
Hi all,

I've been trying to give a friend of mine an account on my machine so she can ssh in.  I enter

```
useradd -d /home/maria -m -s /bin/zsh -p <password>
```

and it tells me everything's OK.  I try logging in via ssh with the new account -- it doesn't like the password.  So I try 

```
useradd -d /home/maria -m -s /bin/zsh
passwd maria
```

and enter the password.  I enter the same one twice, obviously, so it is set -- but when I try to log in via ssh, again it doesn't like the password.  I tried the same thing with adduser instead of useradd -- same problem.  

At first I figured perhaps it was ssh, but I found that I can't log in on the local machine with any account other than the one that the ubuntu installer created, nor can I 

```
su maria
```

either.  

Anyone have any ideas about what's going on?

Thanks!

---

### Post by gerbman on 2006-08-18
Try adding the user with the User Management gui (assuming you're running GNOME). I just tried that, and was able to ssh into the machine using that account with no problem.

---

### Post by ifishfortorque on 2006-08-18
I don't have a GUI at the moment -- if that's the only way to get it to work, I'll install one, but it seems silly to do this.  I always assumed the GUI was just doing useradd/adduser in the background anyway, but I could be wrong.

---

### Post by aysiu on 2006-08-18
Have you tried *adduser* instead of *useradd*?

---

### Post by ifishfortorque on 2006-08-18
> I tried the same thing with adduser instead of useradd -- same problem. 

I also tried both useradd and adduser without specifying a password, and I tried to ssh in without a password.  No good.  I then added a password using passwd, and again couldn't log in any way I tried.

---

