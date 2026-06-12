---
title: "Desktop effects over 1024x768"
date: 2007-05-10
forum: Desktop Environments
---

### Post by lynxus on 2007-05-10
Hi guys,

Little problem here.

I cant seem to get desktop effects to work correctly over 1024x768 res.

When it goes over that it runs fine,BUT there is a big verticle line on the right hand sid eof my screen that does a hall of mirrors type effect when a windo goes over it.

My xorg.conf is using "radeon"
My GFX card is ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]

Any ideas?



Here is a picture of what im seeing, This happened on fedora aswell :( so it must be some config issue somewhere.
[IMG]http://www.putfile.com/pic.php?img=4218835[/IMG]

[http://www.putfile.com/pic.php?img=4218835](http://www.putfile.com/pic.php?img=4218835)

---

### Post by Memory.Dump on 2007-05-10
are you using the ATI drivers from their site? if not try getting those I had something odd happen wtih my geforce until I got their drivers and ran them

---

### Post by lynxus on 2007-05-10
Yes tried them aswell.

---

### Post by jester45 on 2007-05-10
is your card supported by "ati" i tihnk its beter

---

### Post by lynxus on 2007-05-11
ive figured it out.

gotta hcnage my colour depth to 16 , it wont run int 24bit

---

