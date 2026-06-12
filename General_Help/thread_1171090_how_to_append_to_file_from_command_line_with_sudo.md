---
title: "how to append to file from command line with sudo?"
date: 2009-05-27
forum: General Help
---

### Post by quickk on 2009-05-27
Hi everyone, 

I'm writing a script and want to do this:

```
echo 'new_repository' >> /etc/apt/sources.list
```

This fails because I don't have the permission to do so.  I've tried these alternatives, which have failed also:

```
sudo echo 'new_repository' >> /etc/apt/sources.list
```
```
sudo echo 'new_repository' sudo >> /etc/apt/sources.list
```

How can I do this?

Thanks!

---

### Post by SgtPepperKSU on 2009-05-27
```
echo 'new_repository' | sudo tee -a /etc/apt/sources.list
```

Should do it.

---

### Post by quickk on 2009-05-27
Cool!  Thanks!

---

