---
title: "No Vim 7? What the heck!?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by necro351 on 2006-08-07
I find it startling that there is no vim 7 package on synaptic for dapper drake. Am I missing something? Is there any effort on making a vim 7 package? If so then maybe somebody could point me to the project web page.

---

### Post by cantormath on 2006-08-07
> **necro351 said:**
> I find it startling that there is no vim 7 package on synaptic for dapper drake. Am I missing something? Is there any effort on making a vim 7 package? If so then maybe somebody could point me to the project web page.

did you try adding the universe repository, 
```
sudo gedit /etc/apt/sources.list
```
and look
then
start synaptic and reload.  when I cant find stuff I generally check other repos.

---

### Post by necro351 on 2006-08-07
This is the line from my sources file:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted

Even with universe packages, there is no vim 7, strange no?

---

### Post by isharra on 2006-08-07
I believe vim 7 is in edgy. So you get to wait but it is coming :)

---

### Post by Tortanick on 2006-08-07
Why not apt-get remove vim --purge then compile it yourself?

---

### Post by llamakc on 2006-08-07
There's no reason to remove the deb of it at all. Just build it in $HOME or /usr/local and use update-alternatives to add it as the system default editor (or set the variable in .bashrc).

---

### Post by glennric on 2006-10-14
Try adding the following to your sources.list
```

# Seveas' packages (GPG key: 1135D466)
deb http://mirror2.ubuntulinux.nl dapper-seveas all
deb-src http://mirror2.ubuntulinux.nl dapper-seveas all

```

Vim 7 is there.

---

