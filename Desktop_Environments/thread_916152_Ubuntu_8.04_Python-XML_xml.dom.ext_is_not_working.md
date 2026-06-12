---
title: "Ubuntu 8.04 Python-XML xml.dom.ext is not working"
date: 2008-09-10
forum: Desktop Environments
---

### Post by shahansudu on 2008-09-10
hi all,
   I'm trying to use the 'xml.dom.ext' module in Python to print a XML document into a file. But in my desktop which runs Ubuntu 8.04, Python does not recognize the module. I looked in /urs/lib/python2.5/site-packages/oldxml to see whether the module exist and I can see the ext module under dom but I cant import it. The pathe is also in sys.path. I saw that many tools broke after switching to 8.04 but other than alternatives to ext I dont see a permanent solution to including ext in sys.path. Only solusion I found failed. Does anyone know of a solution?

---

### Post by kwtm2 on 2008-10-14
I had the same problem.  I solved it by adding these two lines before you import the package:

[B]import sys
sys.path.append('/usr/lib/python%s/site-packages/oldxml' % sys.version[:3])[/B]

I was able to find the following info by Google.  It is from 
*http://blog.mypapit.net/2008/05/ubuntu-hardy-python-xml-error.html*
(click here: [http://blog.mypapit.net/2008/05/ubuntu-hardy-python-xml-error.html](http://blog.mypapit.net/2008/05/ubuntu-hardy-python-xml-error.html))
It is NOT from me!  I just copied and pasted. 

--( start )--
[I]I found out that in Ubuntu Hardy, the python-xml package has moved xml.dom.ext.* package to /usr/lib/python2.5/site-packages/oldxml thus breaking python code which depended on python-xml.

One way to work around this bug is to append :

sys.path.append('/usr/lib/python%s/site-packages/oldxml' % sys.version[:3])

just before you import stuff from xml.dom.ext.*. Hope that would help you.[/I]
--( end )--

---

