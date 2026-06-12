---
title: "No root login after upgrade"
date: 2006-07-21
forum: Desktop Environments
---

### Post by razor7 on 2006-07-21
Hello...after a really good Upgrade from 5.10 to 6.06 i can not log in to Root account using GDM. I have enabled admin acces trough GDM but each yime i want to login the login session simply restarts, like pressing ctrl+alt+bkspc.

Any idea?


Thanks a lot


PD: I have to say...really goood version...look and feel great!

---

### Post by wieman01 on 2006-07-22
I think there is no more "root" login available... You will have to log on to your system and use "sudo" or "su" command to act as root. For security reasons they have disabled it which I think is a good feature.

---

### Post by razor7 on 2006-07-22
Yes..i know that...and I also know that this can be overrided, because I have udsed 5.10 version for almost 9 months and I was able to login without any problems using GDM and root account, but after the upgrade...I can still login to root accout using SHELL but I cant do that using GDM even activating ROOT LOGIN option in the preferences...

That is my question...how can I re-enable ROOT graphical login...

Thanks a lot...

---

### Post by razor7 on 2006-07-24
Hello...no clue on this issue...Please advise...

---

### Post by Kilz on 2006-07-24
> **razor7 said:**
> Hello...no clue on this issue...Please advise...
my advice is to use ```
gksudo nautilus
```to launch the file manager as root if you need a gui.

---

### Post by razor7 on 2006-07-24
Thanks a lot...but in the previus version of Ubuntu, I have not done that...and even if I try that....it trhows an error...

Please I want to login as root, graphically, like any other distribution..even like any other UBUNTU distribution...

Please advise.

---

### Post by wieman01 on 2006-07-24
Perhaps this is something you could do (although I have not tried it yet, I quite like the new security concept of Ubuntu).

Create a new user (name different from root) and assign it to the "root" user group. Then log on to the system with the new user account. Does that work?

---

### Post by Jagot on 2006-07-24
[https://help.ubuntu.com/community/RootSudo#head-7bd7cf735bf6b1cfac9464a9331775eaadc8b8ec](https://help.ubuntu.com/community/RootSudo#head-7bd7cf735bf6b1cfac9464a9331775eaadc8b8ec)

---

### Post by Kilz on 2006-07-24
There is always someone who will sell a gun to someone intent on suicide.

---

### Post by wieman01 on 2006-07-24
> **Kilz said:**
> There is always someone who will sell a gun to someone intent on suicide.

Haha... True. I would avoid this as well, but hey, if you have a fresh copy of Ubuntu on your computer with no personal files installed what can happen?! 

I agree, I would rather refrain from log on with root authority. But we were asked, right? :-)

---

### Post by kazuya on 2006-07-25
Thanks for the tip. I'll take my chance. Sudo is great, but extremely cumbersome to deal with when a user or admin is trying to do certain administrative tasks.

It is great practice to never log in and use root for day to day PC use, but for administrative functions like creating users, changing window managers, backing up user datas before a repartitioning or testing purpose of something new like e17, etc.. This is the way to go.

This is what I like about mepis and slack over Ubuntu. But with this guide, more access to the tweaking is available.

Thanks again. Everything is about choice. It really bothers me when someone knows how to help someone to a question they ask, but refuse to help but give another method that they prefer with no regards to the user's circumstance.

You can say be warned, use this method instead, but if you insist on doing this, then do this. Not force your way of doing things on the user. 

This is just my opinion and I am sure the opinion of the poster and the nice gentleman kind enough to give this great tip on enabling root.

You should notice that the guide also states how to later disable the root login.

This informs the user of the inherent risk associated with this ease of administrative power {root.}

Having said mepis and slack, there is a reason I am on Ubuntu over the slack for example. That is large package availability, polish, and more importantly the great community of Ubuntu. I really kept Ubuntu after dapper 6.06 LTS. It blew me away. Prior, it was Mepis and Vector Soho 5.1.

---

### Post by wieman01 on 2006-07-25
> **kazuya said:**
> Thanks again. Everything is about choice. It really bothers me when someone knows how to help someone to a question they ask, but refuse to help but give another method that they prefer with no regards to the user's circumstance.

Nicely said. I must agree that I had the same thought when reading this post. I am on the same page.

---

