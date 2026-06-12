---
title: "im new, how do i install games?"
date: 2005-06-10
forum: Gaming &amp; Leisure
---

### Post by bmwboy on 2005-06-10
OK, i downloaded a game package, a linux package from a site, how do i install it?

---

### Post by The Na Kun on 2005-06-10
Right click on the tar.bz2/tar.gz and click extract here.  Right click on desktop and open the "big T." put in:
cd [path]
./configure
make
sudo make install

But if it is a .deb, just put in:
sudo dpkg -i [path]

If you meant something else, then say.  Your post didn't say much...

---

### Post by bmwboy on 2005-06-10
ok, i open root terminal and dothat:
it says :
no rule to make target. stop

---

### Post by bmwboy on 2005-06-10
[QUOTE=The Na Kun]Right click on the tar.bz2/tar.gz and click extract here.  Right click on desktop and open the "big T." put in:
cd [path]
./configure
make
sudo make install

But if it is a .deb, just put in:
sudo dpkg -i [path]

If you meant something else, then say.  Your post didn't say much...[/QUOTE]
i was leaving, so i rushed it, heres more detail:
I download supertux oackage, and run apt-get
I just want to install supertux, its in directory:
/home/bmwboy/

---

### Post by digby on 2005-06-10
What kind of file was it that you downloaded?  .deb?  .tar.gz? something else?  There are several different ways to install files, and if you can tell us exactly what it is you downloaded, we can help.

One thing that I noticed:  you mentioned downloading the package and then running apt-get.  Apt-get is great for automatically downloading and installing programs.  For instance, if you wanted the program foobar, you would just run:
```
sudo apt-get install foobar
```
It will search for, download, and install the program (and any related dependencies for you).  Ubuntu also provieds a graphical tool called Synaptic to help you with this that resides under the System menu (I think... if it's not sorry... I use KDE).

---

### Post by GrumpySimon on 2005-06-10
What is the package called? something.tar.gz, something.tgz, something.tar.bz2, something.deb, something.package? 

--Simon

---

### Post by bmwboy on 2005-06-11
[QUOTE=GrumpySimon]What is the package called? something.tar.gz, something.tgz, something.tar.bz2, something.deb, something.package? 

--Simon[/QUOTE]
x86.package

---

### Post by gil-galad on 2005-06-11
try double-clicking on it

---

