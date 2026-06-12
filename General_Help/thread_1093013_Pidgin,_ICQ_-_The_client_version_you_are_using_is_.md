---
title: "Pidgin, ICQ - The client version you are using is too old"
date: 2009-03-11
forum: General Help
---

### Post by _ppr on 2009-03-11
Couple days ago I got the follwing message when I connected to ICQ usint piding
```
The client version you are using is too old. Please upgrade at http://pidgin.im
```

I downloaded and compiled Pidgin2.5.5 (latest version) from [http://pidgin.im](http://pidgin.im), but got the same error

What should I do ?

---

### Post by rokixz on 2009-03-11
> **_ppr said:**
> Couple days ago I got the follwing message when I connected to ICQ usint piding
```
The client version you are using is too old. Please upgrade at http://pidgin.im
```

I downloaded and compiled Pidgin2.5.5 (latest version) from [http://pidgin.im](http://pidgin.im), but got the same error

What should I do ?

Same problem too on Linux Mint and Kubuntu. In Kopete everything's working fine.

---

### Post by The-RaveN on 2009-03-11
Hi.

You should follow the steps in:
[http://developer.pidgin.im/ticket/8612](http://developer.pidgin.im/ticket/8612)


Basically - close pidgin, uninstall any pidgin/libpurple you may have, than make clean, ./configure, sudo make install and (!!!) sudo ldconfig (for loading the new libraries you just installed).
After that just run pidgin and you're good to go.

G.

---

### Post by whitethorn on 2009-03-11
I also had the same problem.  I got it to work, with pidgin from [www.getdeb.net](www.getdeb.net) just search for pidgin.  You have to download 4 packages.  Before you install them remove your old version of pidgin.

```
sudo apt-get remove pidgin
```

Then install using the debs.

---

### Post by _ppr on 2009-03-11
Thanks

For me works the following

 - sudo apt-get remove pidgin
 - compile pidgin (I used this instructions - [http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783) - note use 2.5.5 (not 2.5.4))
 - sudo ldconfig

---

### Post by sadrak on 2009-03-11
is this markes as a bug? So we will get a automatic update in some days? Or must i follow one of the fixes?

---

### Post by binbash on 2009-03-11
Today there was a pidgin update at repos.

---

### Post by yadayada2 on 2009-03-11
But not for 8.04 :(

---

### Post by sjrixon on 2009-03-11
Cool.. Working again in 8.10 :)

---

### Post by ianchristie on 2009-03-11
Just refreshed the repos in 8.04 and there's a pidgin update. Although, the about box says 2.4.1 but it appears to connect to ICQ fine now.

---

### Post by sanakan on 2009-03-13
No, i can't see any update in ubuntu 8.04...

Or is it just on my computer? I refresh 1000 times a day to check. I even changed between US and swedish servers to see if there's a difference :(

Ah well, if there will eventually be a working update, i will just wait. [-o<

I was just curious if you 8.04-users have got one working update yet.

---

