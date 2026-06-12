---
title: "Installing synaptic packages"
date: 2009-06-01
forum: General Help
---

### Post by StarThorn1 on 2009-06-01
I want to install openSSL with synaptic packages. I see it in the list but it also has a bunch of other stuff too that I don't know if I need. 

Some of the items listed have a green mark in them. Does this mean they go together or does it mean I already have them?

---

### Post by zonination on 2009-06-01
> **StarThorn1 said:**
> I want to install openSSL with synaptic packages. I see it in the list but it also has a bunch of other stuff too that I don't know if I need. 

Some of the items listed have a green mark in them. Does this mean they go together or does it mean I already have them?

I believe openSSL is already installed by default, which is why a few of them might have a green checkmark next to them. If it's not installed, then you can go to terminal and type:

```
sudo apt-get install openssl
```

I hope this helps.

Cheers!
-Zoni

---

### Post by prem1er on 2009-06-01
> **StarThorn1 said:**
> I want to install openSSL with synaptic packages. I see it in the list but it also has a bunch of other stuff too that I don't know if I need. 

Some of the items listed have a green mark in them. Does this mean they go together or does it mean I already have them?

If the box next to the package is filled in green, it means that the package is already installed.  openSSL is already included in Ubuntu.  If you need to install something else the package manager will take care of any dependencies that are required.

---

### Post by nebileix on 2009-06-01
Synaptics include dependencies by itself.

Some packages need those to work. So its fine.

---

