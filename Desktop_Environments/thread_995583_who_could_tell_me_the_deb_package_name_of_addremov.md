---
title: "who could tell me the deb package name of add/remove"
date: 2008-11-28
forum: Desktop Environments
---

### Post by mythmgn on 2008-11-28
I carelessly used apt-get command to remove a deb package,and it  removed the 'add/remove' in the applications menu as well.
   please tell me what's the deb package name of it in order that i could reinstall it.
   thanks

---

### Post by Cyhawk on 2008-11-28
Heh =)

synaptic is what your looking for.

---

### Post by sstusick on 2008-11-28
Type this in the terminal: > sudo apt-get install synaptic


That should get it back.

---

### Post by mythmgn on 2008-11-28
I didn't mean the synaptic based on gtk,I have it.I mean that when you click the menu 'application',and you will see a add/remove softwares .That's it.I just lost it.

---

### Post by sstusick on 2008-11-28
You could try right clicking on the menu > edit menu and see if it's listed there. If it is, just select the box next to it, if it isn't already. If it is, I don't know then, sorry.

---

### Post by ganesh4it on 2008-11-28
Hi am new to Ubuntu forum and also working with linux..,

i dont know from where i can rise the new thread(mak e new post)...plz help me...


Also i need your help to install "nautilus-open-terminal 0.8"..
am trying past three day am not able to install.....

its very urget plzz help me out...,

:popcorn:

---

### Post by the yawner on 2008-11-28
> **mythmgn said:**
> I carelessly used apt-get command to remove a deb package,and it  removed the 'add/remove' in the applications menu as well.
   please tell me what's the deb package name of it in order that i could reinstall it.
   thanks

Try:
```

sudo apt-get install gnome-app-install

```
or just search for the package *gnome-app-install*.

=====
> **ganesh4it said:**
> Hi am new to Ubuntu forum and also working with linux..,

i dont know from where i can rise the new thread(mak e new post)...plz help me...

Look for the link New Thread to create your own thread and kindly avoid hijacking other threads in the future. As for your issue:

> 
Also i need your help to install "nautilus-open-terminal 0.8"..
am trying past three day am not able to install.....

its very urgent plzz help me out...,
```

sudo apt-get install nautilus-open-terminal

```

---

### Post by mythmgn on 2008-11-28
> **the yawner said:**
> Try:
```

sudo apt-get install gnome-app-install

```
or just search for the package *gnome-app-install*.

=====

Look for the link New Thread to create your own thread and kindly avoid hijacking other threads in the future. As for your issue:


```

sudo apt-get install nautilus-open-terminal

```
Thank you very much,I got it with your hints.

---

