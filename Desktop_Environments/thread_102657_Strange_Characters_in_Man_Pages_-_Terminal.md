---
title: "Strange Characters in Man Pages - Terminal"
date: 2005-12-12
forum: Desktop Environments
---

### Post by gkchicago on 2005-12-12
Hello, I have seen this before on other linux distributions and am seeing it on a "server" install of ubuntu that I did today.  On the man pages and even while I'm compiling programs I see the "â" character.  I am an english speaker in the USA and I think I selected the correct language parameters when installing..  the "â" is all over the man pages so I assume it is being substituted for something but I can't be sure what.

I'm guessing its some kind of charset issue?  Thank you for your time.

---

### Post by gsgleason on 2007-12-04
edit /etc/default/locale and change the line

LANG="en_US.UTF-8"

to

LANG="es"

log out and log back in and look at some man pages.

---

### Post by maybeway36 on 2007-12-04
Why change language to Spanish?

---

### Post by reason2007 on 2008-02-26
I found an easy fix to this. Add the following line to your .bashrc file in your user home directory. 

alias man='man -E ascii'

For more info on the command see "man man" I found this fix on the site below..

[http://www.jamescooke.info/blog_archive/category/linux/ubuntu/]("http://www.jamescooke.info/blog_archive/category/linux/ubuntu/")

---

