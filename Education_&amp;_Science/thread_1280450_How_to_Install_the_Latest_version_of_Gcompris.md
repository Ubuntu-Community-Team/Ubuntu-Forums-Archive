---
title: "How to Install the Latest version of Gcompris"
date: 2009-10-02
forum: Education &amp; Science
---

### Post by trellis2 on 2009-10-02
GCompris is a high quality educational software suite comprising of numerous activities for children aged 2 to 10. It's translated into over 40 languages. I use it to learn other languages and the kid can use it too ;). As of Oct/01/2009 GCompris in the Jaunty repositories doesn't work. It's an old version with an unsatisfied dependency. Installing python-numeric will fix it.
Code:
**sudo apt-get install python-numeric** but this only give you an experimental version. It would be better to install the latest version, which is easier said than done. Here is a method that worked for me.
Download gcompris from [http:////sourceforge.net/project/downloading.php?group_id=6865&filename=gcompris-8.4.12.tar.gz&a=93275535]("http:////sourceforge.net/project/downloading.php?group_id=6865&filename=gcompris-8.4.12.tar.gz&a=93275535") 
while that is downloading  open a terminal and run these commands to get all dependencies met :**you@yourComputer~$ sudo apt-get install libgnet-dev libgnet2.0-0 python-pysqlite2** and 
 **you@yourComputer~$ sudo apt-get build-dep gcompris**
After the download completes change to the directory where you downloaded compris-8.4.12.tar.gz **you@yourComputer~$ cd /wher/ever/it/is/gccompris-8.4.12.tar.gz**
**you@yourComputer~$tar -xvf gcompris-X.X.tar.gz**
**you@yourComputer~$cd gcompris-x.x.x**
**you@yourComputer~$sh configure**
**you@yourComputer~$sudo make**
**you@yourComputer~$sudo make install**
Now test the install to see that it's working properly
**you@yourComputer~$gcompris**
You can create a lancher icon using the launcher.

---

### Post by hubie on 2009-10-02
Thank you for this info.  I haven't upgraded my laptop yet, but my kids love Gcompris and they'd be quite upset if I upgraded and broke the program. :)

---

### Post by joshzam on 2009-10-11
Thanks for the walk-through. Very useful!

---

### Post by j.h.klein on 2011-05-05
Thanks but I consistently get the error message:
config.status: error: cannot find input file: `autopackage/Makefile.in'
at the end of "configure",
Any hint ?

---

### Post by Jlb181 on 2011-12-28
I was able to install gcompris 11.12 on Ubuntu 11.10 using this information.  And again later on a second Ubuntu 11.10 64 bit machine.Everything works.  At least with gCompris, I have not to this point noticed any problems with my Ubuntu 11.10.  The installation upgraded 9.6.1 to 11.12.

sudo apt-get install libgnet-dev libgnet2.0-0 python-pysqlite2

and (I did have to build the dependencies)

Download the archive [gcompris-X.X.tar.gz]("http://sourceforge.net/projects/gcompris/files/") then: 
  tar -xvf gcompris-X.X.tar.gz 
  cd gcompris-X.X 
  sh configure 
  Analyse, the errors, install the missing dependancies. Often you will have to install the -devel packages on your distribution. On Ubuntu or Debian, you can get all the build dependancies with the command &#8217;apt-get build-dep gcompris&#8217;.

Then run: 
  make 
  make install

---

### Post by daniroma on 2012-03-19
Works for me too, as Jlb181 describes. Well done.
Xubuntu 11.10

---

