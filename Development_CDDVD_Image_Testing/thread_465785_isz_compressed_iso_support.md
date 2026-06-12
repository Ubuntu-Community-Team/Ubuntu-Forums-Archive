---
title: "isz compressed iso support"
date: 2007-06-06
forum: Development CD/DVD Image Testing
---

### Post by aldeby on 2007-06-06
Dear Ubuntu community, 
is there any support in linux for ISZ compressed CD/DVD image?

The format has been developed by ezbsystems, the creator of UltraISO, and due to its open format (specs are available at [http://www.ezbsystems.com/isz/iszspec.txt]("http://www.ezbsystems.com/isz/iszspec.txt") ) it is already supported by a few applications in windws such as DaemonTools image mounting utility.

Is there any way to mount these images here? 
Running Ultraiso via wine works, but no image mounting is possible, furthermore being a compressed format the standard loop mounting should not work.
Thank you for your support!

---

### Post by jmesmon on 2009-06-28
> EZB Systems offers a free license for certain technological aspects described above under certain restrictions 
and conditions. A free SDK package is also available. Please contact EZB Systems at [email]isz@ezbsystems.com[/email] with 
regard to acquiring a license.


Unfortunately, while it does *seem* to be open (though i cannot confirm that it is documented correctly), EZB evidently feels they have a patent/some legal control over the information. 

If anything, you will probably get a isz2iso program, not mounting support. (unless it is possible to write a fuse fs for it, which may or may not be do able)

---

### Post by turgidtoupee on 2010-03-09
Hi, I know this is an old topic, but you can convert these with anytoiso running under wine. I've got the latest version of wine and haven't tested any others, but I can confirm it works.

---

### Post by damnated on 2010-07-21
> **turgidtoupee said:**
> Hi, I know this is an old topic, but you can convert these with anytoiso running under wine. I've got the latest version of wine and haven't tested any others, but I can confirm it works.
It works indeed, thanks for posting :popcorn:

---

### Post by monet.hart on 2010-09-08
it is difficult to indeed get mounting suupport

---

