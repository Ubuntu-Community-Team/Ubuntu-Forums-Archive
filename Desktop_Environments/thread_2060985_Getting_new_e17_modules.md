---
title: "Getting new e17 modules"
date: 2012-09-21
forum: Desktop Environments
---

### Post by scoon on 2012-09-21
Hey there, 

Is there a deb for other e17 modules?

Thanks, 

Skip

---

### Post by Frogs Hair on 2012-09-21
I was using this PPA which was updated often  and functioned much better(for me ) than the repo packages. If you choose to use it remove the repo packages and the .e folder in home hidden folders first.Bodhi Linux is a Ubuntu based E17 distro and tested updates come from their repository. 

[http://www.bodhilinux.com/](http://www.bodhilinux.com/) 



```
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
sudo apt-get update
sudo apt-get install e17

```

---

### Post by scoon on 2012-09-21
> **Frogs Hair said:**
> 
```
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
sudo apt-get update
sudo apt-get install e17

```

Hey there, 

That was the ticket.

Thanks, 

Skip

---

### Post by Frogs Hair on 2012-09-21
Once the ppa is installed more modules are available in synaptic which don't come with core packages in the repo.

---

