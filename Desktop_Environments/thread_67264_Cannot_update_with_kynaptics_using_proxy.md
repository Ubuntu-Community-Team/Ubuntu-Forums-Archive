---
title: "Cannot update with kynaptics using proxy"
date: 2005-09-19
forum: Desktop Environments
---

### Post by gizmoz on 2005-09-19
Hello,
I installed Kubuntu v5.04 and loved it. Now I am trying to solve everyday issues like ...update.
-
My internet connection is through a proxy on a windows machine. Setting up internet connection was easy and few minutes later Konqueror was browsing web pages.
-
Next thing I tried to do is use kynaptics and find new packages for my shiny new linux machine. I uncommented a few lines in /etc/apt/sources.list: 
deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
-
I saved the file and tried to ''refresh package information from repositories'' in Kynaptics. It quickly passes some urls and I get some error popups in alien language (might be a font problem with Greek language only in error popups). apt-get displays a ''temporarily anavaliable'' for the urls it tries to reach and aptitude displays alien characters too.
-
So my guess is that it has something to do with the use of a proxy.  Have you any ideas of what can I do to inform kynaptics about using my proxy pc as a gateway? 
-
Thank you

---

