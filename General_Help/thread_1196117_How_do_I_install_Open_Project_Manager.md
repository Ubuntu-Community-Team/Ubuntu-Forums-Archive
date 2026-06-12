---
title: "How do I install Open Project Manager"
date: 2009-06-24
forum: General Help
---

### Post by saskatchewan on 2009-06-24
There is a way to install Open Project Manager from the Synaptic but I forgot how to do it.

I have downloaded the file from the site but can not figure out how to install it.

Can someone tell me?

---

### Post by nice_like_rice on 2009-06-24
What type of file is it?

edit: from looking at the site it looks like source code, compile it :). Other ways of installing it would be adding a line to your sources.list then using aptitude, if it's .deb then use dpkg -i, or otherwise chmod +x then ./ ?

---

### Post by saskatchewan on 2009-06-24
it does not say, it is in a zip file and when I extract it there are some files.  two of them jar.

That is why I wanted the command line installation.

---

### Post by nice_like_rice on 2009-06-24
java -jar filename

?

---

### Post by saskatchewan on 2009-06-24
I am not sure about java jar but here is the website that I got if from.

[http://openprojectmanager.com/](http://openprojectmanager.com/)

---

### Post by nice_like_rice on 2009-06-24
Ok, I just downloaded the file. You're not downloading the source code are you? When I unzip the file (openpm1.10.1.zip), there are no .jar files contained, there are 3 txt files and 1 .war file.#

edit: 
did you read that page: [http://openprojectmanager.com/web/help?id=installation](http://openprojectmanager.com/web/help?id=installation)
If so which steps are you having problems with?

---

### Post by saskatchewan on 2009-06-24
what should I do with the files that I downloaded

---

### Post by nice_like_rice on 2009-06-24
Follow the instructions on that page, it tells you what to do. I expect you're having this problem when trying to install tomcat, I can't see where else you would get the .jar files from?

This link may help
[http://www.eglug.org/book/export/html/1630](http://www.eglug.org/book/export/html/1630)

---

### Post by saskatchewan on 2009-06-24
I looked around the site and found a deb package version that installed really easily.

---

