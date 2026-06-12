---
title: "Problems with Stellarium"
date: 2009-04-23
forum: General Help
---

### Post by nacholand on 2009-04-23
Hi there,

I've installed Stellarium (the last version I guess, from the repositories) in my Ubuntu 8.04, but this problem comes out when I executed it from the console.
I thought it could be Compiz giving me a hard time since I have a poor graphics card, but no. I turned it off and it was the same.

Here's the output:

[FONT="Lucida Console"][B]stellarium: main/renderbuffer.c:2153: _mesa_reference_renderbuffer: Afirmación `oldRb->Magic == 0xaabbccdd' fallida.
Cancelado[/B][/FONT]

Anybody had the same problem? 
Any help is needed and apreciated.

Cheers :)

---

### Post by gordonh on 2009-05-07
I've just tried to run Stellarium for the first time and Iget  the output posted below.

The "failure 2" repeats for ever.  I suspect I should raise a bug report but I thought i would be better to check it out on the forums first.



Loaded 230 / 230 common star names 
Loading star names from "/usr/share/stellarium/stars/default/name.fab" 
Loaded 3215 / 4359 scientific star names 
Creating GUI ... 
try_pbo_zcopy: failure 2
try_pbo_zcopy: failure 2
try_pbo_zcopy: failure 2
try_pbo_zcopy: failure 2
try_pbo_zcopy: failure 2

---

