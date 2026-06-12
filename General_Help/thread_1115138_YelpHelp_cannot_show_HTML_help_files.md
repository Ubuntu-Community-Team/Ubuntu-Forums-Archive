---
title: "Yelp/Help cannot show HTML help files"
date: 2009-04-03
forum: General Help
---

### Post by reef2dive on 2009-04-03
When I use Yelp to list a help file which is an HTML file I get the following response e.g.:
"The file &#8216;/usr/share/doc/lame/html/index.html&#8217; could not be read. This file might be missing, or you might not have permissions to read it."

The file exists and the permission are 
-rw-r--r-- 1 root root  2113 2008-07-25 12:40 index.html

If I open the file in a web browser there are no issues. I have re-installed ubuntu-docs with no difference. There are *.omf files that are supposed to define the behaviour of yelp. However I cannot find the documentation regarding this.

What I am looking for is information on how to correct the problem and how to add other HTML files to yelps database. The man page for yelp is not very conclusive to me.

Any help is very much appreciated.

---

### Post by ajgreeny on 2009-04-03
Can you open the html help file by right clicking and choosing yelp from the "Open with" context menu, or will it not open at all in yelp?  And just out of interest, why does it matter and why not use Firefox to view the file?

---

### Post by reef2dive on 2009-04-04
True, I can open the files in a Browser. That is not the issue. What I want is to have one common point for all the documentation, independant of format, as I have other help files in HTML format. 

It looks like some rights setting. As seen the file exists. However starting Yelp as root, does not make a difference, the message is the same.
Opening the file by right-clicking on the file and chosing Yelp gives the same error as previously.

---

