---
title: "How do I make a document in the root?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by nzk on 2006-08-21
It keeps saying I do not have enought permissions](*,)

---

### Post by utab on 2006-08-21
1 cd /
2 sudo mkdir directory-name
  pass:...

Have fun

---

### Post by nzk on 2006-08-21
> **utab said:**
> 1 cd /
2 sudo mkdir directory-name
  pass:...

Have fun

I mean a document not a directory :confused:

---

### Post by frenkel on 2006-08-21
Why do you wan't to make a document there? It's not meant for saving your documents. You should store your documents in your home directory.

---

### Post by nzk on 2006-08-21
Because a tut I was reading said make ~/.Xsession

which I assumed to be the document .Xsession in the root

---

### Post by utab on 2006-08-21
> **nzk said:**
> Because a tut I was reading said make ~/.Xsession

which I assumed to be the document .Xsession in the root

~/.Xsession
|
|-->Not the root, this is the /home/user, you are going to create a hidden file under home, like .bashrc, .bash_profile...

---

### Post by frenkel on 2006-08-21
> **nzk said:**
> Because a tut I was reading said make ~/.Xsession

which I assumed to be the document .Xsession in the root

~ means your homedirectory. Open up a terminal and type cd ~. You'll end up in your homedirectory, see?

---

