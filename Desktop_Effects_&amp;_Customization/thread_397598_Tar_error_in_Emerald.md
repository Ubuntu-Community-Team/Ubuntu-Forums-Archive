---
title: "Tar error in Emerald"
date: 2007-03-30
forum: Desktop Effects &amp; Customization
---

### Post by tymanthius on 2007-03-30
I'm loving beryl in Fiesty, but when I try to grab from the repositories, it gives tar errors.  I searched around, but couldn't find a fix.

Thanks!

---

### Post by raja on 2007-03-30
It is not clear what your question is? What are you trying to get from the repositories ? And what is the error you get ?

---

### Post by jsteve54302 on 2007-04-16
I believe tymanthius is referring to the message boxes declaring "Error calling tar." with no further information when clicking on the Fetch [...] Themes buttons under the Repositories tab in Emerald Themer.  I have had this problem in Kubuntu 6.10 Edgy and Kubuntu 7.04 Feisty.  This seems to be a result of a few corrupted theme tarballs on the svn repository containing the themes, and only affects the corrupted themes (visit the Beryl support ticket[ http://bugs.beryl-project.org/ticket/1470]("http://bugs.beryl-project.org/ticket/1470") for more details).  If you can find the original theme files and decompress them by hand with gzip, then untar them with tar, you should get the missing themes, but hopefully somebody will fix the files Real Soon Now.

---

