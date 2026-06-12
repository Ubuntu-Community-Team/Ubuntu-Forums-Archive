---
title: "Headers file  in /usr/include"
date: 2009-05-25
forum: General Help
---

### Post by nehagupta on 2009-05-25
Hello i want to pates some c headers file in usr/include but paste option is disabled . How can i do this.( I tried to change permission but perhaps it didnt work)
Moreover how can i include the headerfile which are not already in /usr/include ( I want to use openssl headers file)

---

### Post by taurus on 2009-05-25
If you want to copy files to /usr/include, you need root privilege.

```
sudo cp filename.h /usr/include
```
Otherwise, run nautilus and you can drag 'n drop to wherever you want.

```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lloyd_b on 2009-05-25
> **nehagupta said:**
> Hello i want to pates some c headers file in usr/include but paste option is disabled . How can i do this.( I tried to change permission but perhaps it didnt work)
Moreover how can i include the headerfile which are not already in /usr/include ( I want to use openssl headers file)

I would recommend *against* manually installing anything into /usr/include.  

For openssl, installing the package "libssl-dev" should provide the needed headers.  "sudo apt-get install libssl-dev" in a terminal window, or via the package manager of your choice, to install it.

Lloyd B.

---

### Post by nehagupta on 2009-05-25
When i tried sudo apt-get install libssl-dev following output came
reading package lists ...Done
building dependency tree
Reading state information...Done
E:**could,nt find package libssl-dev**

---

### Post by lloyd_b on 2009-05-25
> **nehagupta said:**
> When i tried sudo apt-get install libssl-dev following output came
reading package lists ...Done
building dependency tree
Reading state information...Done
E:**could,nt find package libssl-dev**
Which version of Ubuntu are you using?  That package *should* be there.

Try opening up Synaptic (or another GUI package manager), and searching for it (or something with a similar name) in there...

Lloyd B.

---

