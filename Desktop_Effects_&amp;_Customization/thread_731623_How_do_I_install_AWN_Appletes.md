---
title: "How do I install AWN Appletes?"
date: 2008-03-22
forum: Desktop Effects &amp; Customization
---

### Post by thenetduck on 2008-03-22
Hi 

I would like to install this applete

[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=895&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=895&page=1&isLive=true)

but I can't figure out how. Also, I saw a Mac4Lin thing that had a neat fan out type of feature "stacks" I think Apple calls it. Does anyone know how to get AWN to do that? 

Thanks a bunch

the Net Duck

---

### Post by reyhan on 2008-03-22
try this open terminal and edit sources file list

```
    deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
    deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

and put this in the end of line 

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

and get the repositories key

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
```
```
sudo apt-key add reacocard.asc
```
```
rm reacocard.asc
```

and this ```
sudo apt-get update
```

and install the AWN ```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

i hope thats work

---

### Post by reyhan on 2008-03-22
if thats doesn't work go to this link [COLOR="Red"][http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")[/COLOR]

---

### Post by ayoli on 2008-03-22
As reacocard how linked above said, repository at tuxfamily has moved to ppa.
The repo for awn is now :
```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
```
or for hardy
```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

---

### Post by thenetduck on 2008-03-23
Sorry for the confusion but I have AWN installed, I just would like to some how install the applet or addon or whatever it is so that I can have features like my workspace in the doc or the applications manager in my doc. 

Thanks 
The Net Duck

---

### Post by thenetduck on 2008-03-23
> **reyhan said:**
> try this open terminal and edit sources file list

```
    deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
    deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

and put this in the end of line 

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

and get the repositories key

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
```
```
sudo apt-key add reacocard.asc
```
```
rm reacocard.asc
```

and this ```
sudo apt-get update
```

and install the AWN ```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

i hope thats work
Oh thank you so much, this worked wonderfully! I guess I didn't install it correctly the first time. Thanks a million! 

The Net Duck

P.S. To anyone reading this and doing this, this code installed all the extra apps I was looking for! ;)

---

### Post by tooferson5 on 2008-07-12
how do i authenticate my awn install so i dont get the NOT AUTHENTICATED warning during updates.  i am using ubuntu hardy64.  thanks in advance.

---

