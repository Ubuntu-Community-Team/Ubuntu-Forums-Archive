---
title: "Username change...please."
date: 2006-11-28
forum: Forum Feedback &amp; Help
---

### Post by justinjstark on 2006-11-28
I would like to change my username to

justinjstark

Would an admin out there be willing to do this for me?  I would appreciate it.  Thanks.

---

### Post by catlett on 2006-11-28
You can just add another user with that username and give the new user administration powers. Then just select thyat user at login.
Add the new user
```
sudo useradd justinjstark
```
Thne add justinjstark to the admin group so he will have sudo powers
```
sudo adduser justinjstark admin
```

You can delete the old user after you make the new user with (that is if you want to. You could keep them both. It's up to you)
```
sudo userdel oldname
```

---

### Post by justinjstark on 2006-11-28
Sorry, I meant forum username.

---

### Post by PriceChild on 2006-11-28
> **catlett said:**
> You can just add another user with that username and give the new user administration powers. Then just select thyat user at login.
Add the new user
```
sudo useradd justinjstark
```Thne add justinjstark to the admin group so he will have sudo powers
```
sudo adduser justinjstark admin
```You can delete the old user after you make the new user with (that is if you want to. You could keep them both. It's up to you)
```
sudo userdel oldname
```Slightly off topic now... but I STRONGLY reccomend you to use the gnome gui to perform this operation. There's a few other groups you may like to be a part of that it'll sort out.

Pricey

---

### Post by justinjstark on 2006-11-28
> **catlett said:**
> You can just add another user with that username and give the new user administration powers. Then just select thyat user at login.
Add the new user
```
sudo useradd justinjstark
```
Thne add justinjstark to the admin group so he will have sudo powers
```
sudo adduser justinjstark admin
```

You can delete the old user after you make the new user with (that is if you want to. You could keep them both. It's up to you)
```
sudo userdel oldname
```

BTW: An easier way to do what you're suggesting is with the usermod command.  ```
usermod -l newusername -m oldusername
```  This will simply change the linux username without having to worry about losing your settings or home directory.

But, to clarify, I want a username change ON THESE FORUMS, not on my linux install.  :)

---

### Post by ubuntu-geek on 2006-11-28
Please send me a PM with the new username

---

