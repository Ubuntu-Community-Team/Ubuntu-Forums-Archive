---
title: "help installing kooldock and superkaramba"
date: 2005-05-10
forum: Desktop Environments
---

### Post by tonysathre on 2005-05-10
i got kooldock-0.3 and when i run the ./configure i get this error: 

checking if Qt compiles without flags... yes
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
t0ny@ubuntu:~/kooldock/kooldock$                      

i used synaptic to get all the headers that were available but it still did the same thing.

also i tried installing superkaramba-0.36 and got the same error

checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
t0ny@ubuntu:~/SuperKaramba/superkaramba-0.36$            

what do i need to do to get this error fixed

---

### Post by Kurse on 2005-05-10
I believe its the kde-devel package you are missing

---

### Post by tonysathre on 2005-05-10
thanks dude that worked, i ran the make and make install and it all finished without errors but now i cant execute it. i went into the directory and clicked on the icon to execute it and it said it cant find the executable file. what should i do

---

### Post by nykobing on 2005-05-10
[QUOTE=tonysathre]thanks dude that worked, i ran the make and make install and it all finished without errors but now i cant execute it. i went into the directory and clicked on the icon to execute it and it said it cant find the executable file. what should i do[/QUOTE]


Install the deb from here - [http://www.youmortals.com/ubuntu/packages/kooldock/](http://www.youmortals.com/ubuntu/packages/kooldock/)

---

