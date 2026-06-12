---
title: "How to view .chm files in ubuntu?"
date: 2009-01-22
forum: General Help
---

### Post by prick.i.am on 2009-01-22
How do i open .chm files in linux??
How do i read them?

---

### Post by any.linux12 on 2009-01-22
What kind of file is that? Give me an example

---

### Post by prick.i.am on 2009-01-22
> **any.linux12 said:**
> What kind of file is that? Give me an example

its a microsoft compiled html help file... like online help files...
neways i found "xchm" to open it.
juz dwnloaded it 
$ sudo apt-get xchm

---

### Post by linux_tech on 2009-01-22
By installing a chm viewer

If you are using gnome-
```
sudo apt-get install gnochm
```

(for kde use- kchmviewer)

Run gnochm program-
```
gnochm file.chm
```

---

### Post by prick.i.am on 2009-01-22
> **linux_tech said:**
> By installing a chm viewer

If you are using gnome-
```
sudo apt-get install gnochm
```

(for kde use- kchmviewer)

Run gnochm program-
```
gnochm file.chm
```

thx....

---

### Post by heindsight on 2009-01-22
I usually use archmage
```
sudo apt-get install archmage
```

Then do 
```
archmage -p 4096 file.chm &
```

This causes archmage to run as an http server publishing the contents of the chm file on port 4096. So now you can read the chm file by using your favourite web browser to connect to port 4096 on your machine (in other words by typing localhost:4096 into the address bar). After you're done, you can kill archmage again by doing
```
pkill archmage
```

Archmage has other capabilities too: it can extract the contents of a chm file to give you a directory containing html files or it can use it in conjuction with apache (see the manual for more details).

---

### Post by moster on 2009-01-22
In add/remove programs, search "chm" you will find dozen .chm viewers.

---

### Post by abhilashm86 on 2009-01-22
u can convert chm to pdf using the following,
chm2pdf 
then from pdf its easy to handle

---

### Post by C0pac3t1c on 2009-01-22
Thankx I been looking for this.

---

### Post by prick.i.am on 2009-01-22
> **heindsight said:**
> I usually use archmage
```
sudo apt-get install archmage
```

Then do 
```
archmage -p 4096 file.chm &
```

This causes archmage to run as an http server publishing the contents of the chm file on port 4096. So now you can read the chm file by using your favourite web browser to connect to port 4096 on your machine (in other words by typing localhost:4096 into the address bar). After you're done, you can kill archmage again by doing
```
pkill archmage
```

Archmage has other capabilities too: it can extract the contents of a chm file to give you a directory containing html files or it can use it in conjuction with apache (see the manual for more details).


THX Heindsight.....

---

### Post by prick.i.am on 2009-01-22
> **heindsight said:**
> I usually use archmage
```
sudo apt-get install archmage
```

Then do 
```
archmage -p 4096 file.chm &
```

This causes archmage to run as an http server publishing the contents of the chm file on port 4096. So now you can read the chm file by using your favourite web browser to connect to port 4096 on your machine (in other words by typing localhost:4096 into the address bar). After you're done, you can kill archmage again by doing
```
pkill archmage
```

Archmage has other capabilities too: it can extract the contents of a chm file to give you a directory containing html files or it can use it in conjuction with apache (see the manual for more details).

im not able to open port 4096
It says failed to connect
wat do i do???

---

### Post by heindsight on 2009-01-22
> **prick.i.am said:**
> im not able to open port 4096
It says failed to connect
wat do i do???

Strange, works for me. Make sure that archmage is running and listening on port 4096 when you try to connect.

Check the output of 
```
pgrep archmage
```
and
```
sudo netstat -tvlp
```

---

