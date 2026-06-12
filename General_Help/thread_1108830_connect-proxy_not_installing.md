---
title: "connect-proxy not installing?"
date: 2009-03-28
forum: General Help
---

### Post by abhilashm86 on 2009-03-28
i tried to install connect-proxy, its unable to install, what is the problem? 
```

abhilash@abhi:~$ sudo apt-get install connect-proxy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package connect-proxy

```
i want to use connect-proxy, so tell how to?

---

### Post by dcstar on 2009-03-28
> **abhilashm86 said:**
> i tried to install connect-proxy, its unable to install, what is the problem? 
```

abhilash@abhi:~$ sudo apt-get install connect-proxy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package connect-proxy

```
i want to use connect-proxy, so tell how to?

That package is not in your repositories, you need to add a repository that contains it. Enable the Universe repository in your system and update your package lists.

---

### Post by abhilashm86 on 2009-03-28
> **dcstar said:**
> That package is not in your repositories, you need to add a repository that contains it. Enable the Universe repository in your system and update your package lists.

which repository i need to add? some 3 party and others are already there.

---

