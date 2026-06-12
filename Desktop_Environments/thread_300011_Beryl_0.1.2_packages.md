---
title: "Beryl 0.1.2 packages?"
date: 2006-11-15
forum: Desktop Environments
---

### Post by shoofy on 2006-11-15
Anyone know where I can get Beryl 0.1.2 packages (official or unofficial) for Edgy? I have the "http://ubuntu.beryl-project.org edgy main-edgy" repo in my sources.list, but it still doesn't have the new version.

---

### Post by 23meg on 2006-11-15
Use this repo:
```
deb http://ubuntu2.beryl-project.org/ edgy main
```

---

### Post by loell on 2006-11-15
does this repo requires a public key?

and will this instructions apply  aside from the repo instruction?

[http://www.ubuntuforums.org/showthread.php?t=263851]("http://www.ubuntuforums.org/showthread.php?t=263851")

---

### Post by hesee on 2006-11-15
Is beryl going to be added to official ubuntu repos anytime? If not, why not? I don't like to add new repos wildly to sources.list for every other program.

---

### Post by 23meg on 2006-11-15
Stable releases don't get new software versions, and I can't see it in the Feisty repos or [REVU]("http://revu.tauware.de/"). You can add the repo, install Beryl and then remove it, no big deal, it doesn't have to stay.

---

### Post by Suzan on 2006-11-15
> **loell said:**
> does this repo requires a public key?


Yes, you can add it:

```
wget http://ubuntu2.lupine.me.uk/1609B551.gpg -O- | sudo apt-key add -
```

---

### Post by shoofy on 2006-11-15
Thanks. Got it now. Too bad it didn't fix some of the problems I've been having with it...

---

### Post by 23meg on 2006-11-15
Such as?

---

### Post by machia on 2006-11-15
Seems to work fine, no crashes..yet. Zap&fire effects rock :P

---

### Post by loell on 2006-11-15
> **Suzan said:**
> Yes, you can add it:

```
wget http://ubuntu2.lupine.me.uk/1609B551.gpg -O- | sudo apt-key add -
```

thank you :)

---

### Post by K4P741N KRUNCH on 2006-11-23
Im having trouble with getting that key to work.

Says Name or service is not known.

---

### Post by sddfdds on 2006-11-24
Why can't you see it being in the Fesity repos?  Isn't that exactly where it should go sometime soon?

---

### Post by Ralith on 2006-11-27
beryl-project.org in general seems down to me. Are there any alternative repos?

---

### Post by darrenm on 2006-11-27
Trevino's SVN's work fine for me:

```
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
```

---

### Post by shoofy on 2006-11-27
> **Ralith said:**
> beryl-project.org in general seems down to me. Are there any alternative repos?
From [beryl-project.org]("http://beryl-project.org"): > Server hard drive disk failed on Sunday, and we're currently trying to rescue it even though it does not look good at all. Apologies.

---

### Post by xopher on 2006-11-27
Lupine's repo is still up and running too (with the 0.1.2's)

```
deb http://beryl-mirror.lupine.me.uk/ edgy all
```
And the GPG-key (same as for beryl-project.org) :

```
wget http://beryl-mirror.lupine.me.uk/1609B551.gpg -O- | sudo apt-key add -
```

---

### Post by loell on 2006-11-27
can i get 0.1.3 on trevinos svn? i downloaded from that repo but the splash says 0.1.2 

though in the package it says, beryl 0.1.3+svn20061125-r1422-3v1ubuntu10 :-k

---

