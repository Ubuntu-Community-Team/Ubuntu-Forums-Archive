---
title: "Ispiron 1501: A little help attaining wireless and packet injection?"
date: 2008-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Glubbdubdribian on 2008-09-06
Hi everybody,

I'm new to ubuntu and indeed to anything linux(!) but i wish to learn. I have a Dell Inspiron 1501 and I've installed Hardy Heron on one of my partitions. I've spent two days trying to figure out how to get my wireless working, but to no avail. I have a Broadcom 440x 10/100 Integrated Controller, which i think should use the bm43xx, bm43, and bm43legacy drivers. I would also like to get packet injection working so that I can use aircrack-ng. I've tried many a  walk-through but none were quite right - lol.

As I'm new to this, would you please mind telling me what the bm43xx things ARE, how I can get my wifi to work, and how i could get packet injection working... or at least a link to somewhere which has some answers for me...

sorry, this sounds like an awful lot to be asking, but i need the help. Thank you very much in advance :D

Oh! and btw, I'm trying to connect to WPA - if it makes any difference..

thx :)

---

### Post by Glubbdubdribian on 2008-09-09
bump :)

---

### Post by Dennis N on 2008-09-09
I don't have that particular model myself, but I have seen a guide to 8.04 on the Inspiron 1501:

[http://www.ubuntu1501.com/2008/03/ubuntu-hardy-heron-804.html]("http://www.ubuntu1501.com/2008/03/ubuntu-hardy-heron-804.html")

It may offer some help.

---

### Post by Glubbdubdribian on 2008-09-11
thx very much but i've already tried ndiswrapper - didn't work :(

oh well... it's alright - i think i'm gonna get a new computer anyways... 

thx though :)

---

### Post by mehtdosa11 on 2008-09-12
hi, have you installed the drivers via system/administration/hardware drivers ? 
when i loaded ubuntu on my laptop it automatically picked up the fact i needed restricted drivers for my broadcom wireless and ati graphics components and it loaded them automatically [with a couple of mouse clicks]

---

### Post by shae on 2008-09-12
The hardware you are referring to is the LAN port, not your wifi card.  Post the results of ```
lspci
``` to help us identify your wifi card.

---

### Post by Glubbdubdribian on 2008-11-01
hi, yh the problem was with the drivers as mehtdosa11 thought.
Then i used this guide: [http://tinyshell.be/aircrackng/forum/index.php?topic=3597](http://tinyshell.be/aircrackng/forum/index.php?topic=3597)
worked perfectly.
Thanks for the help :)

---

