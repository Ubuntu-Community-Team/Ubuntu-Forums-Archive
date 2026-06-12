---
title: "write access on first HD"
date: 2009-05-01
forum: General Help
---

### Post by lucifuge on 2009-05-01
apologies if this in the wrong section.

I've recently installed Ubuntu 9.04 as a full install. Physically, I have 2 HDs and a mate told me to use advanced partitioning on install. I set the first and second HD's to mount on '/' and '/home' respectively. When I now use Ubuntu, it seems I am physically accessing the full second HD because of the /home region so I have full writeable access. 

However, where the OS is stored on the first HD, I have a lot of free space, but no ability to create folders etc. Ie i dont have write access as it stands. No doubt this is normal. But how do create a new folder and being able to write to it? Say I want a new folder off the root called /mydata   for example?  (I dont want anty write access to the system folders, just a new one dedicated for my data)

---

### Post by dcstar on 2009-05-01
> **lucifuge said:**
> apologies if this in the wrong section.

I've recently installed Ubuntu 9.04 as a full install. Physically, I have 2 HDs and a mate told me to use advanced partitioning on install. I set the first and second HD's to mount on '/' and '/home' respectively. When I now use Ubuntu, it seems I am physically accessing the full second HD because of the /home region so I have full writeable access. 

However, where the OS is stored on the first HD, I have a lot of free space, but no ability to create folders etc. Ie i dont have write access as it stands. No doubt this is normal. But how do create a new folder and being able to write to it? Say I want a new folder off the root called /mydata   for example?  (I dont want anty write access to the system folders, just a new one dedicated for my data)

```
sudo mkdir /mydata
sudo chown whatever-my-user-name-is /mydata
```

---

### Post by lucifuge on 2009-05-01
> **dcstar said:**
> ```
sudo mkdir /mydata
sudo chown whatever-my-user-name-is /mydata
```

wonderful!   thankyou

---

