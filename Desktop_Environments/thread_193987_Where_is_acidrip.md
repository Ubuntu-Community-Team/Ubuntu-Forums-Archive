---
title: "Where is acidrip"
date: 2006-06-10
forum: Desktop Environments
---

### Post by cazz on 2006-06-10
I have now install Ubuntu Drake but I can't find acidrip in Synaptic?
I have check all repositories

](*,)

---

### Post by zugu on 2006-06-10
Acidrip is in the repos. You might need to enable them. Check [this]("https://wiki.ubuntu.com/AddingRepositoriesHowto") link to learn how to enable them, then do this:```
sudo apt-get install acidrip
```

---

### Post by colsinc on 2006-06-29
I have the same problem as well. I just updgraded to dapper.
  my sources.list is the same as 
[http://www.psychocats.net/ubuntu/sources.php]("http://www.psychocats.net/ubuntu/sources.php")
i did sudo apt-get update
but still can't find acidrip.  

did you solve this problem?

---

### Post by cazz on 2006-06-29
Yes I add the repos from that link that Zugu gave me

---

### Post by ardchoille on 2006-06-29
[QUOTE=cazz]I have now install Ubuntu Drake but I can't find acidrip in Synaptic?
I have check all repositories

](*,)[/QUOTE]
acidrip is in the multiverse repo. Read this on how to enable multiverse:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by jgcamp99 on 2006-06-29
In Applications, Add/Remove, AcidRip is one of those applications that you install post initial OS install. 

For newbies unfamiliar: It's in the other method of installing applications, I understand Synaptic Package Manager to be one method, the other is thru the Applications menu thru the Add/Remove. Then there's building from source manually form tarball source, rpms, debs (the latter two are semi-automatic installations from source tarballs) and the like.

---

