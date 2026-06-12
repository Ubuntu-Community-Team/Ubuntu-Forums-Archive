---
title: "problem with kile,please help"
date: 2007-03-23
forum: Desktop Environments
---

### Post by dominoes on 2007-03-23
when i quickview the .tex file, kile send me the info:

[IMG]http://www.imagehosting.com/out.php/i376377_Picture1.png[/IMG]

I have already installed the kdvishell

any suggestions are welcome!

thanks

---

### Post by lexxonnet on 2007-03-24
I'm not too sure about this itself, but why dont you just use PDFLaTeX and compile it straight to a PDF before viewing it?

This way, you can even open the file in Kpdf, and as you recompile, kpdf updates the view

---

### Post by Achille on 2007-03-24
Be sure that kdvi is installed:

sudo apt-get install kdvi

---

### Post by dominoes on 2007-03-24
thank you and I have done it before, this is the result:

[IMG]http://www.imagehosting.com/out.php/i378291_Picture1.png[/IMG]

any suggestions else?

thanks a lot.

---

### Post by Achille on 2007-03-24
Of course, you have to enable the universe repositories. Don't forget to reload the list of available packages:


sudo apt-get update

---

### Post by dominoes on 2007-03-24
how to enable the universe repositories?

I am new user and have not idea to find it out

thanks

---

### Post by Achille on 2007-03-25
sudo kate /etc/apt/sources.list

and add universe multiverse after main restricted.

For example, my file contains:

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

Save the changes and type the command:

sudo apt-get update

and then 

sudo apt-get install kdvi

should work.

---

