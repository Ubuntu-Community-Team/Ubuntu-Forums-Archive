---
title: "update-manager fails (feisty) (python error)"
date: 2008-07-04
forum: Desktop Environments
---

### Post by caviar on 2008-07-04
The bubble for the update-manager was failing. When the mouse cursor went over, it would say "131 updates available", but when I clicked, I got nothing.

Well, running "update-manager" from the command line generated an error - a *python* error:

ImportError: /usr/local/lib/python2.5/site-packages/PyXML-0.8.4-py2.5-linux-i686.egg/_xmlplus/parsers/pyexpat.so: undefined symbol: PyUnicodeUCS2_Decode

So, I figured out what was happening -

update-manager is supposed to use the python2.5 installed on /usr/bin. Well, I had subsequently installed a whole bunch of stuff in /usr/local (/usr/local/bin/python and /usr/local/lib/python2.5 etc), which I have happily been using for development for a year. I had thought that the two pythons were completely independent. 

Well, I was wrong. When /usr/bin/python2.5 runs, *by default*, it adds /usr/local/lib/python2.5 to its path - and apparently there are things in /usr/local which are inconsistent with those at /usr/lib (not suprising).

I have fixed the problem - but I had to modify the actual update-manager file itself. At the beginning, I set the path in python *explicitly* to not include the /usr/local stuff.

But this is clearly a kludge. My question: how do I keep the Ubuntu python stuff at /usr/bin/python2.5 from adding /usr/local/lib/python2.5 to the import search path in a clean and global way? I really want both pythons completely isolated from one another!

Thankyou.

---

