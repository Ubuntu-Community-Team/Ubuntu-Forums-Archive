---
title: "libxaw header files"
date: 2006-02-03
forum: Desktop Environments
---

### Post by maxdevis on 2006-02-03
when i want to install gxine (./configure) with the package from there website it says:

configure: error: you need to install libxaw header files (-dev package)


i need to install it from there website, because apt-get says it's the latest version(0.4.4) but it isn't(0.5.4).

but when i do sudo apt-get install libxaw7 it says everything is installed?

what can i do?

---

### Post by Perfect Storm on 2006-02-03
```
sudo apt-get install libxaw7-dev
``` should do it.

why don't you grab gxine from the repo?
```
sudo apt-get install gxine
``` (need to enable universe first)

---

### Post by maxdevis on 2006-02-03
he couldn't find that.

when i do
sudo apt-get install libxaw7

he says everything is installed

---

### Post by maxdevis on 2006-02-03
[QUOTE=Artificial Intelligence]
why don't you grab gxine from the repo?
```
sudo apt-get install gxine
``` (need to enable universe first)[/QUOTE]

he says it's up to date, but that's the 0.4.4 and i want the 0.5.4

---

### Post by Perfect Storm on 2006-02-03
[QUOTE=maxdevis]he couldn't find that.

when i do
sudo apt-get install libxaw7

he says everything is installed[/QUOTE]


yeah, but he need the libxaw7-dev for compiling.

---

### Post by Perfect Storm on 2006-02-03
[QUOTE=maxdevis]he says it's up to date, but that's the 0.4.4 and i want the 0.5.4[/QUOTE]

ah, okay...I missed that part :P

---

### Post by maxdevis on 2006-02-03
ok,

there was somthing wrong with my sources.list

i fixed that and could install the libxaw, but now i got this error:

configure: error: libjs not found

---

### Post by Perfect Storm on 2006-02-03
```
sudo apt-get install libjs0 libjs0-dev
```

---

### Post by maxdevis on 2006-02-03
when i install libjs i get this error

No `START-INFO-DIR-ENTRY' and no `This file documents'.
install-info(/usr/share/info/js.info.gz): unable to determine description for `dir' entry - giving up


but when i do then 
sudo apt-get install libjs0 libjs0-dev

he says everything is installed


but when i want to install gxine he says
configure: error: libjs not found

---

### Post by Perfect Storm on 2006-02-03
Try with 
```
./configure --prefix=/usr --enable-gtk2 
```

---

### Post by maxdevis on 2006-02-03
nope

doesn't work.

i don't have to reinstall libjs with other parameters cause of the "error" with the installation?

---

### Post by Perfect Storm on 2006-02-03
odd...I just tried install the same file as you to see if I get the same message error. Same here.....

---

### Post by maxdevis on 2006-02-03
hmmm

the install instructions tells about a configure.in but i can't find that file.

"The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'."

---

### Post by maxdevis on 2006-02-03
found it

it works when you have spider-monkey installed.

---

