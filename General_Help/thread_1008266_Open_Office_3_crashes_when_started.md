---
title: "Open Office 3 crashes when started"
date: 2008-12-11
forum: General Help
---

### Post by erezz on 2008-12-11
Hi,

I've installed open office 3 (on my kubuntu 8.10) according to the instructions here: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

Whenever I run oowriter, it tries to recover an untitled doc. No matter if I decide to recover it or skip that, open office crashes. I tried to delete ~/.openoffice.org, but that didn't help. Any idea?

Thanks,
Erez

---

### Post by Arup on 2008-12-11
Have you installed any extensions? Also what version Java are you using, for any extensions like Language tools, witers tools etc. it needs and only works on Sun Java and not Open JDK, try installing Sun Java and see if the problem goes away.

---

### Post by erezz on 2008-12-14
So, I removed openJDK. Here's my current java version:

[erez.zilber@erez-lx:~]$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.3.2

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Still, I get the same crash.

Erez

---

### Post by wally80 on 2008-12-14
Hi!

I also get the same error on Kubuntu 8.10 64bit!
I am currently searching in the forum. If I find something I link it here.

ciao,
Dan

UPDATE:
It seems we are not the only one: [http://www.nabble.com/OpenOffice-3.0---currently-broken-td20922309.html](http://www.nabble.com/OpenOffice-3.0---currently-broken-td20922309.html).
The package openoffice.org-kde 3.0.0-6  seems to be broken.
I removed it and openoffice works perfectly...

cheers

---

### Post by erezz on 2008-12-15
yeah, works for me too.

Thanks,
Erez

---

### Post by zloy_alenko on 2008-12-15
i've got same problem too in kde, but in gnome everything works fine.
After uninstalling openoffice.org-kde OOo starts normally in kde, but now panel buttons disapear after moving mouse over them :)

---

### Post by Monkeybells on 2008-12-16
I've the same problem.

Here's a link to another post that shows a temporary fix for the openoffice.org-kde package problem: [http://ubuntuforums.org/showthread.php?t=993516&highlight=untitled+crash+openoffice.org-kde&page=6](http://ubuntuforums.org/showthread.php?t=993516&highlight=untitled+crash+openoffice.org-kde&page=6)

I'll be trying-out the fix myself when I'm back on my linux machine.

You'll find the suggested fix on the 5th or 6th page. It seems that several people have had joy from it.

---

### Post by benoitg on 2008-12-18
> **zloy_alenko said:**
> i've got same problem too in kde, but in gnome everything works fine.
After uninstalling openoffice.org-kde OOo starts normally in kde, but now panel buttons disapear after moving mouse over them :)

I have the same symptoms.  They will disapear if you uninstall openoffice.org-gtk.  The widgets won't be pretty, but they will work properly.

---

### Post by abn91c on 2008-12-21
removing that file  openoffice.org-kde, works for kubuntu 8.10:P

---

