---
title: "user corrupt"
date: 2007-04-17
forum: Desktop Environments
---

### Post by jjakspaw6 on 2007-04-17
Hi, 


My user account became corrupt, when I type in my user name and password the log on window tells methe user doesn't exist! I enabled the root account and can log in that way but when I create a new user it simply disappears!  I know I don't have a whole lot of info here but can someone point me in the right direction to create a new user..... 

Thanks  
Jason

---

### Post by taurus on 2007-04-17
What are the outputs of these two commands from a prompt?

```
df -h
ls -la /home
```

---

### Post by Juissi on 2007-05-22
> **jjakspaw6 said:**
> 
My user account became corrupt, when I type in my user name and password the log on window tells methe user doesn't exist! I enabled the root account and can log in that way but when I create a new user it simply disappears!  I know I don't have a whole lot of info here but can someone point me in the right direction to create a new user..... 
Jason

I hope you have already found a solution. Anyway, this just happened to me too, creating a new user with a specific name didn't didn't do anything. I found out that you have to remove the problematic user's group, for example user is 'jack' -> remove group 'jack'. After this the user can be created again.

---

