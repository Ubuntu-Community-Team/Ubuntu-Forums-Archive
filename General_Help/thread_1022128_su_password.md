---
title: "su password"
date: 2008-12-26
forum: General Help
---

### Post by smallroad on 2008-12-26
Hello,  

I'm following instructions to install Java for firefox and need to login as su but don't seem to have the password?

When I installed Ununtu I don't recall being asked to enter an su password? I did enter a password which I am prompted for every time my laptop tries to connect to my wireless network (which is a question for another day) but that password does not work for su?

I can't believe I was prompted for an su password and have forgotten it, is it possible I have not set an su password yet?

Hope someone can help...

smallroad

---

### Post by oilchangeguy on 2008-12-26
> **smallroad said:**
> Hello,  

I'm following instructions to install Java for firefox and need to login as su but don't seem to have the password?

When I installed Ununtu I don't recall being asked to enter an su password? I did enter a password which I am prompted for every time my laptop tries to connect to my wireless network (which is a question for another day) but that password does not work for su?

I can't believe I was prompted for an su password and have forgotten it, is it possible I have not set an su password yet?

Hope someone can help...

smallroad

when you installed ubuntu you were asked to set up a user name, and password. that password is also your su password.

---

### Post by Dr Small on 2008-12-26
Ubuntu does not setup a root password by default. You can use this instead:
```
sudo
```

Append sudo to the beginning of your command that require root privileges, and it should work. Do some more reading on sudo, here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Dr Small

---

### Post by smallroad on 2008-12-26
Thanks Dr Small that certainly enabled me to complete my Java installation, still a little unclear about the whole su thing but will read the link you have posted. :)

smallroad

---

