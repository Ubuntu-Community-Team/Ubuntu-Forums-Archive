---
title: "games frozen bubble"
date: 2005-01-16
forum: Gaming &amp; Leisure
---

### Post by jstam1999 on 2005-01-16
i would like to be able to play the frozen bubble game on ubuntu but don't know how
to start. i don;t have it on my computer and am new at linux. if someone could tell me
how to find the game and how to install and run it, i would be grateful. i have a hp
pavilion ze 4530 notebook computer and everything seems to work on it.

---

### Post by node on 2005-01-16
on CLI(shell interface) 'sudo apt-get install frozen-bubble'
That is, if you've enabled warty universo in your apt sources.

---

### Post by jstam1999 on 2005-01-16
i tried sudo apt-get install frozen-bubble, and i got a response that said "can't find
package frozen-bubble" i must be doing something wrong.  i tried it from terminal
program and  put  my password when asked

---

### Post by node on 2005-01-16
make sure the lines ```
deb http://archive.ubuntu.com/ubuntu warty universe
 deb-src http://archive.ubuntu.com/ubuntu warty universe

``` are un-#'ed in your /etc/apt/sources.list
after that, do an apt-get update && apt-get install frozen-bubble

---

### Post by ixus_123 on 2005-01-16
& to be able to edit that list you'll need to open an editor with root permissions so
/etc/apt/sources.list
sudo gedit

for example, you can navigate to the file from there.

---

### Post by jstam1999 on 2005-01-16
i don't know whether to say thanks or not. i did edit the * out of the files and it still
didn't work, but it said to get apt update. which i did and then it downloaded okay.
now it plays great but i just wasted about half an hour playing it. hard to control that
habit.

---

### Post by ixus_123 on 2005-01-16
you always have to update after changing the list or indeed downloading anything.  When you update, apt-get, fetches an uptodate list of what's available.  If you don't update your system will things were as they were the last time you ran apt-get.

Might also want to try **lbreakout2** if you want great gaming

---

### Post by multipunto on 2005-02-18
[QUOTE=node]make sure the lines ```
deb http://archive.ubuntu.com/ubuntu warty universe
 deb-src http://archive.ubuntu.com/ubuntu warty universe

``` are un-#'ed in your /etc/apt/sources.list
after that, do an apt-get update && apt-get install frozen-bubble[/QUOTE]

Thanks you!!!
 :-)

---

### Post by taurus8585 on 2005-02-23
Hi all...

May i know how to get the game frozen bubble working on linux? I'm trying to download the the '.rpm' files from the [www.frozen-bubble.org](www.frozen-bubble.org) website but don't know which files to use.

---

### Post by IceAxe18 on 2005-02-23
taurus8585 you need to do this to install the game:
 
apt-get update
apt-get install frozen-bubble

---

### Post by taurus8585 on 2005-02-24
_Can Not Find SDL.pm  _ 

Managed to install the frozen-bubble but when I tried to run the frozen-bubble I get this error: 
Can't locate SDL.pm in @INC (@INC contains: /usr/lib/perl5/5.8.0/i486-linux /usr/lib/perl5/5.8.0 /usr/lib/perl5/site_perl/5.8.0/i486-linux /usr/lib/perl5/site_perl/5.8.0 /usr/lib/perl5/site_perl .) at /usr/bin/frozen-bubble line 51. BEGIN failed--compilation aborted at /usr/bin/frozen-bubble line 51. 

Is this due to some missing files or package and what should I do to fix this problem?

---

### Post by jdodson on 2005-02-25
fwiw, it seems from the main frozen bubble page they are going to release a multiplayer network version sometime.  i hope this comes out within the year, it would be a great addition to the game.

---

### Post by prince_niceguy on 2009-02-02
> **node said:**
> on CLI(shell interface) 'sudo apt-get install frozen-bubble'
That is, if you've enabled warty universo in your apt sources.

Thanks you ... was searching for it and never realised that it was in the repo... thanks a ton...

---

### Post by bapoumba on 2009-02-02
This thread was referring to frozen-bubble 2005, closing here :)

---

