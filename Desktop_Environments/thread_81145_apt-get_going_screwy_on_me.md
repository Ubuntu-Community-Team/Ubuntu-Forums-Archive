---
title: "apt-get going screwy on me"
date: 2005-10-23
forum: Desktop Environments
---

### Post by jimmygoon on 2005-10-23
I still don't understand Linux.

This morning I was playing with it and had messed it up pretty well... but had it to the point where I was able to "sudo apt-get install fluxbox" and "sudo apt-get install blackbox"

but now.. after I reinstall Breezy... and I do apt-get flux/black box... I get NOTHING

and nothing in "sudo apt-cache search flux"



---

How do I regain access to those types of downloads?!

thanks

---

### Post by Kyral on 2005-10-23
Did you try a "sudo apt-get update"?

---

### Post by gillion on 2005-10-23
you need to run this command after a fresh install .... 

**sudo apt-get update**

you also need to enable the other software repositories.

you can do this using **synaptic.**

it is also advisable after a fresh install to clean your apt-cache.

---

### Post by jimmygoon on 2005-10-23
[QUOTE=gillion]you need to run this command after a fresh install .... 

**sudo apt-get update**

you also need to enable the other software repositories.

you can do this using **synaptic.**

it is also advisable after a fresh install to clean your apt-cache.[/QUOTE]


I did the **sudo apt-get update** before... with no luck whatso ever.

I don't know what you mean by other software repositories and 

I tried to figure out how to clean the apt-cache but whats the command for that. BTW: Even packages that I KNOW the names of... don't work...

---

### Post by Kyral on 2005-10-23
Check this out for adding repos

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28Repos%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28Repos%29)

---

