---
title: "Paranoid about root?"
date: 2006-01-11
forum: Desktop Environments
---

### Post by pars on 2006-01-11
Hi, 

I'm new and I like Ubuntu very much. 

But there is a **default** root passwd. 
I don't understand this. 

Can someone guarantee that nobody
knows the root passwd? It is randomly 
generated upon each installation? If so,
how long is it?
 

Thanks!
pars

---

### Post by dabang on 2006-01-11
hi pars,

as far as I know, there is no default root password in ubuntu (or any other linux dsitro I know...). In Ubuntu the root account is deactivated by default, but the first user which is created during installation may gather root privileges by using "sudo". So, for example, typing
```
sudo apt-get update
```
will ask for a password, but this is not the root password, but the password of this first user. If you want to activate the root account type
```
sudo passwd root
```.

---

### Post by GeneralZod on 2006-01-11
The following is good reading for how Ubuntu deals with root:

[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)

---

### Post by jrib on 2006-01-11
[QUOTE=pars]Hi, 

I'm new and I like Ubuntu very much. 

But there is a **default** root passwd. 
I don't understand this. 

Can someone guarantee that nobody
knows the root passwd? It is randomly 
generated upon each installation? If so,
how long is it?
 

Thanks!
pars[/QUOTE]

The root account is 'locked'.  Read 'man passwd', specifically the 'Account maintenance' section (after it loads the man just press: /Account maintenance, and then press enter).

---

