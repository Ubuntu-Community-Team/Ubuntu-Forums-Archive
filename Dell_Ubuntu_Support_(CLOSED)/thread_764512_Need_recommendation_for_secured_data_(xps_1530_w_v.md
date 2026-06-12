---
title: "Need recommendation for secured data (xps 1530 /w vista + ubuntu + mediadirect)"
date: 2008-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jooo on 2008-04-23
Hi,

Just wondering, does anyone have any recommendations for setting up vista + ubuntu + media direct in such a way that I can share data (download directory, media files, thunderbird profile)?

Basically, my main aim is to protect my stuff incase my laptop gets stolen.

Cheers!

---

### Post by chewearn on 2008-04-24
A popular cross-platform encryption tool is [Truecrypt]("http://www.truecrypt.org/").  You can place your files inside the encrypted container.

---

### Post by jooo on 2008-04-25
Thanks for the suggestion. I'll have a look into truecrypt. 
Cheers!

Edit: So say if i have 5 partitions (vista, ntfs-share, /, /home, swap) and have truecrypt encrypt everything except the share (so that mediadirect can access my music + videos), I'd be laughing?

---

### Post by chewearn on 2008-04-25
> **jooo said:**
> Thanks for the suggestion. I'll have a look into truecrypt. 
Cheers!

Edit: So say if i have 5 partitions (vista, ntfs-share, /, /home, swap) and have truecrypt encrypt everything except the share (so that mediadirect can access my music + videos), I'd be laughing?

I would say use Truecrypt for the shared data instead.  Being multi-platform, you can then use the truecrypt container in both OSes.

In addition, Truecrypt version 5 now support full Windows encryption.  However, the full linux OS encryption is not available.

So, Truecrypt can be used in two out of three scenarios.

For encrypting Linux OS, you can look for the OS native encryption.  One example (note: I have not tried this, use at your own risk):
[http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

My opinion is that OS encryption is too much trouble, especially since I don't work in a top secret job.  I only go as far as encrypting data.

---

