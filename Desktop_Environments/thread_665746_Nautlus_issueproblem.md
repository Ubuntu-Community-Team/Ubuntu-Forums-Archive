---
title: "Nautlus issue/problem"
date: 2008-01-12
forum: Desktop Environments
---

### Post by CanonKen on 2008-01-12
I've been doing a bit of testing/helping someone today with a program but one part of it wouldn't work for me, turned out I had no Desktop folder in my Nautilus directory.
What I'd like to ask is

1. Can you open a terminal window and enter:  
cd $HOME/.gconf/apps/nautilus

then type ls -l and post your results

2. Any ideas why I have no Desktop folder?

Heres my result

```
ken@ubuntu:~$ cd $HOME/.gconf/apps/nautilus
ken@ubuntu:~/.gconf/apps/nautilus$ ls -l
total 8
-rw------- 1 ken ken    0 2007-11-07 22:15 %gconf.xml
drwx------ 2 ken ken 4096 2007-12-16 20:59 list_view
drwx------ 2 ken ken 4096 2008-01-12 17:34 preferences
ken@ubuntu:~/.gconf/apps/nautilus$ 
```

---

### Post by b0rka7a on 2008-01-12
Here's mine:
```
linuxa@linuxa-ubuntu:~$ cd $HOME/.gconf/apps/nautilus
linuxa@linuxa-ubuntu:~/.gconf/apps/nautilus$ ls -l
total 20
drwx------ 2 linuxa linuxa 4096 2008-01-07 21:59 desktop
-rw------- 1 linuxa linuxa  137 2007-12-24 12:34 %gconf.xml
drwx------ 2 linuxa linuxa 4096 2007-12-26 16:50 icon_view
drwx------ 2 linuxa linuxa 4096 2008-01-12 18:43 list_view
drwx------ 2 linuxa linuxa 4096 2008-01-12 20:15 preferences
linuxa@linuxa-ubuntu:~/.gconf/apps/nautilus$ 
```
And you're missing icon_view along with desktop :-| I have no idea how you can fix it, unless you create them yourself :)

---

### Post by CanonKen on 2008-01-12
Thanks b0rka7a, can't understand whats going on here, I haven't deleted it I'm sure of that :confused:

---

### Post by CanonKen on 2008-01-12
Any more?
I want to find out if its just me thats without it and if so WHY :confused:

---

### Post by jnylen on 2008-01-13
Try:
sudo apt-get install --reinstall nautilus
(and maybe nautilus-data also.)

---

### Post by CanonKen on 2008-01-13
I've just re-installed using Synaptic and nothing has changed, will try with sudo apt-get install --reinstall nautilus later

---

### Post by CanonKen on 2008-01-13
> **jnylen said:**
> Try:
sudo apt-get install --reinstall nautilus
(and maybe nautilus-data also.)
Just done both of them and still no Desktop in there
Anyone any ideas as to why??

---

### Post by psychicdragon on 2008-01-13
why not just mkdir ~/Desktop ?

There's nothing magic about the Desktop folder, it's not required to exist (I don't have one).

---

### Post by b0rka7a on 2008-01-13
I'm interested too about why you don't have a Desktop folder ?
:lolflag:

---

### Post by psychicdragon on 2008-01-13
Because I don't like **** on my desktop.

---

### Post by b0rka7a on 2008-01-13
> **psychicdragon said:**
> Because I don't like **** on my desktop.

:lolflag:

But do you deleted it or it's missing by default ? And if it's missing by default, why I have it ?

---

### Post by psychicdragon on 2008-01-13
I deleted it. There's no sense in having an empty folder in my home that I'm never going to use.

---

### Post by CanonKen on 2008-01-13
> **psychicdragon said:**
> why not just mkdir ~/Desktop ?

There's nothing magic about the Desktop folder, it's not required to exist (I don't have one).
I could do but wondered why it wasn't there, Like I said in 1st post I was doing some testing for someone and the program didn't work because that directory wasn't there, we are just curious to find out why and if others have it missing
Looks like it's not just me now

---

