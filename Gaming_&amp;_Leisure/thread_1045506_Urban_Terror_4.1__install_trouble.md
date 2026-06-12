---
title: "Urban Terror 4.1  install trouble"
date: 2009-01-20
forum: Gaming &amp; Leisure
---

### Post by marcgh on 2009-01-20
Hi,
I am running UBUNTU 8.10.
I downloaded the .deb package of urban terror 4.1

Wen installing, using the package installer, I get the following message:
ERROR: DEPENDENCY IS NOT SATISFIABLE: libopenalOa

Try'd to install this in terminal, then I get this:

user@user-ubuntu:~$ sudo apt-get install libopenal0a
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libopenal0a is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libopenal1
E: Package libopenal0a has no installation candidate

I guess I have to somehow link the software to point to libopenal1 but I don't have the slightest idea how.

Thanks in advance for any help/advice

---

### Post by marcgh on 2009-01-21
anybody? please?

---

### Post by NewJack on 2009-01-21
IDK where you got the .deb from, but you could follow the directions to add the PlayDeb repos to your software sources and Urban Terror is in the list of available games.  After adding the repos, do a refresh and UT should be there.  Easy as pie.

[http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by marcgh on 2009-01-21
Thank you NewJack,
currently not on my ubuntu machine but surely I will try this during the night.

---

### Post by NewJack on 2009-01-22
Just so you know, I am running 8.10 and just installed UT via the PlayDeb repos and had no issues whatsoever.  Should work for you too.

---

### Post by aheckler on 2009-01-22
I would advise installing UrT the "official" way (ie, downloading and extracting the zip file into /usr/local/games). That has never steered my wrong, although your dependency issue might need to be fixed.

---

### Post by fluxlizard on 2009-01-22
Simplest way is just download the zip, unzip it into a folder in your home folder and play it directly from there...

---

### Post by OakGill on 2009-07-09
> unzip it into a folder in your home folder and play it directly from there  hi, i'm very new to the whole "ubuntu" thing, and i was wondering if anyone could give me a step by step walkthrough on how to get the game urban terror from the .zip file i downloaded?

thanks - Oak

---

