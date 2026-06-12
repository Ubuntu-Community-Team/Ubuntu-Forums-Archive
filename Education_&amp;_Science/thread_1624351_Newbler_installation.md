---
title: "Newbler installation"
date: 2010-11-17
forum: Education &amp; Science
---

### Post by Rohan on 2010-11-17
Hi,
Just wanted to know if anyone has had any luck getting Newbler (Roche 454 assembler) in Ubuntu. If you have could you share how you got it going?

Thanks

---

### Post by brdido on 2010-11-24
Yes I did in my desktop, but i can't install it in my servers and i have no idea why.

A get the error : "One of the following libraries was not found : zlib.i386, libXi.i386, libXtst.i386, libXaw.i386"

Are you with the same problem?

---

### Post by brdido on 2010-11-29
Problem solved:

sudo apt-get install ia32-libs

---

### Post by jwhitney on 2010-12-11
[B]The problem appears to be that the Newbler software is a 32-bit program getting run on a 64-bit system.  

Another user (Cappy) posted a thread a while back recommending getlibs, which automatically solves dependencies for 32-bit programs on 64-bit systems. Here is his whole thread, which lists a bunch of usage commands:
[URL="http://ubuntuforums.org/showthread.php?t=474790"]
http://ubuntuforums.org/showthread.php?t=474790[/URL]
[/B]

INSTALL Get-libs

Download getlibs-all from 
[http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)


Once downloaded (in ubuntu), software manager will prompt for an install.  Then in a terminal command: 

getlibs
this will download the 32-bit libraries and dependencies.  Afterwards, retry the Newbler (gsAssembler) setup and it should work fine. 
[SIZE=3][/SIZE]

---

### Post by frogotronic on 2012-11-29
Hi,

  Actually, NEWBLER is not a 32 bit program.  It is 64-bit.  The GUI is 32-bit, but the program itself is 64 bit.  So,...if you want to use the GUI, you have to have 32 bit libraries installed.

- CH

---

### Post by frogotronic on 2012-11-29
Here's a guide: [http://seqanswers.com/forums/showthread.php?t=25339](http://seqanswers.com/forums/showthread.php?t=25339)

---

### Post by overdrank on 2012-11-29
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

