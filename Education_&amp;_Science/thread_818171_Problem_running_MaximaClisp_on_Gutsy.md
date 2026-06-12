---
title: "Problem running Maxima/Clisp on Gutsy"
date: 2008-06-04
forum: Education &amp; Science
---

### Post by Buzzdee on 2008-06-04
Hello, 

I'm running Maxima/Clisp on Gutsy 64-bit on my Thinkpad T61p. I installed both packages from Synaptic. Clisp starts from the terminal and Maxima starts fine, too. But the maxima server doesn't start, therefore I get a timeout at some place. This happens, when I start maxima with clisp: 
brandb@Buzzdee:~$ maxima -l clisp
exec: 145: /usr/lib/maxima/5.12.0/binary-clisp/lisp.run: not found

I have no idea where to start here, since normally the Synaptics-installed programmes run fine :)

Any ideas?

Cheers, 
Bastian

---

### Post by Buzzdee on 2008-06-06
GCL seems to work:

brandb@Buzzdee:~$ maxima -l gcl

Maxima 5.12.0 [http://maxima.sourceforge.net](http://maxima.sourceforge.net)
Using Lisp GNU Common Lisp (GCL) GCL 2.6.7 (aka GCL)
Distributed under the GNU Public License. See the file COPYING.
Dedicated to the memory of William Schelter.
This is a development version of Maxima. The function bug_report()
provides bug reporting information.

Now my problem is that wxMaxima won't get a connection to maxima, please refer to my post in the wxMaxima forums for the complete information: [https://sourceforge.net/forum/message.php?msg_id=5011671]("https://sourceforge.net/forum/message.php?msg_id=5011671")

Cheers, 
Bastian

---

### Post by Buzzdee on 2008-06-12
anyone?

---

