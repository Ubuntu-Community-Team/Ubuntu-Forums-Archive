---
title: "deleting form command line??"
date: 2009-03-05
forum: General Help
---

### Post by beanco on 2009-03-05
Yeha, I know is is possible, I know it has been asked but I am having problems specifically with getting rid of Deluge.

somebody please throw this dog a bone... what is the command for wiping out Deluge via the CL?

Thanks

Robi

---

### Post by chamber on 2009-03-05
Have you tried,

```
sudo apt-get --purge -remove deluge
```

or 

```
sudo apt-get remove deluge-torrent 
sudo apt-get remove deluge
```

---

### Post by beanco on 2009-03-05
Chamber,

I have tired the last on your list

and got this...

```
sudo apt-get remove deluge
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge

```

Time to try the others...


Robi

---

### Post by beanco on 2009-03-05
this seems to have worked.


```
sudo apt-get remove deluge-torrent 
```

thanks


now to start a thread on remove, vs, delet, vs purge. etc.


robi

---

### Post by chamber on 2009-03-05
Your welcome.

---

