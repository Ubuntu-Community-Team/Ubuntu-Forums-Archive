---
title: "How to install software - an overview (repository, .deb, .rpm, source)"
date: 2006-09-10
forum: Desktop Environments
---

### Post by andiii on 2006-09-10
1) Introduction
2) repository
3) .deb
4) .rpm
5) install from compiled source-code
6) .run
7) .bin
8) .jar
9) ...


##########################################

### 1)
Hi, during my first weeks of ubuntu I ran into lots of different ways for installing software.

There is apt-get, aptitude, synaptic, alien usw...

So this topic should help to find a suitable method for every software you want to install. (And uninstall)

### 2)
**repository**: I use synaptic for "big things", to get information about the packages and dependencies before I install. If I'm lazy, I use apt-get install..
I have never used aptitude. Maybe someone who uses it can comment on the advantages of doing so?
> **mscman said:**
> Aptitude does a much better job than apt-get at tracking dependencies. For example, if you install a metapackage such as kde-desktop, all of the files that that package depends on are installed with it. When you use apt-get and you go to uninstall, you'll only be able to remove that metapackage, not the dependencies as well. There are still files left on your computer. When you use aptitude, however, all of the packages, including dependencies, are removed. This results in a much "cleaner" system. I *highly* recommend using aptitude instead of apt-get.
Here is a nice comparison: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) ..
So aptitude is really what should be used!

### 3)
**.deb**: dpkg -i xyz.deb
to uninstall: dpkg -r program

### 4)
**.rpm**: I use alien to make a .deb package, then as above.
alien xyz.deb --> produces .deb package

### 5)
**source**: I had luck with some, and others I couldn't get to work (like the new XFCE, it keeps telling me that dependencies like Pango are not there even that I installed them)..
How do you do it?

tar xvf program.tar.gz 
cd program
./configure (to run configure script if present.. here I'm not sure when to use which --prefix=/opt/xyz or whatever parameter.. so I don't give any prefix most of the time..)
make (to compile)
make check, make clean (not really sure how important, when/why to use)
sudo checkinstall

The last command needs the "chekinstall" program to be installed. I use checkinstall and not "make install", because the removal of checkinstall programs ist easier (just dpkg -r program).

What if you didn't use checkinstall before and want to remove a programm that you installed with "make install"?
> **mcpish said:**
> 
What you could do in your situation is simply recompile the same version of the program you compiled, but install it via checkinstall this time.  Since it's still the same version of the software you already have installed, the new deb file will merely re-install over all the existing files that were installed on your first compile but this time there will be a record of these files in a package (deb file) that is accessible from Synaptic.  Then after it's installed, you can simply un-install the programme in Synaptic and choose the option to "completely remove" it.  This should remove all traces of the programme on your system and all of the associated files.  You can then install the other version of the same programme via synaptic (2 entries will be listed, both your compiled version of the programme and the older version in the ubuntu repositories).

### 6)
**.run**: This is most likely an installer. Just run (double click or ./program.run)

### 7)
**.bin**: same as 6), this is ~ like .exe :)

### 8)
**.jar**: I use a program (JabRef) that comes as a java package like this. Usually I used to run it with "java -jar Jabref.jar", but this command stopped working for some reason.
So I figured out a workaround:

Putting thi in my shell.cfg (bashrc or whatever you wanna call it)
alias jabref='javaws ~/bin/jabref.jnlp'

.. and then downloading Jabref.jar. jabref.jnlp (and maybe install "javaws") I can run it.



### 9)
Another tip:
Maybe it would be good to keep a txt file with all the programs installed. Just in case there is no entry in the menu. Honetsly, I don't remember what cool programs I installed two weeks ago. ](*,) 

---
Of course this won't always work, it's far from perfect and complete, as I am still a beginner. Every software may have it's own perfect way to install and it is especially recommended to read the instructions (README or INSTALL or on the website)..

I just wanted to give a little overview, knowing that this thread would have helped me very much when I started with ubuntu. Because now I have lots of packages installed with just "make install" and lost track a little bit. :)

Comments and suggestions appreciated.

---

### Post by meng on 2006-09-10
When installing from source, or from non-repo debs, you may get the dependencies not satisfied message because your installed version is not deemed acceptable. This can happen because the package is named differently, and/or the version number is an Ubuntu version number.

---

### Post by mscman on 2006-09-10
> **andiii said:**
>  I have never used aptitude. Maybe someone who uses it can comment on the advantages of doing so?

I'd love to! Aptitude does a much better job than apt-get at tracking dependencies. For example, if you install a metapackage such as kde-desktop, all of the files that that package depends on are installed with it. When you use apt-get and you go to uninstall, you'll only be able to remove that metapackage, not the dependencies as well. There are still files left on your computer. When you use aptitude, however, all of the packages, including dependencies, are removed. This results in a much "cleaner" system. I *highly* recommend using aptitude instead of apt-get.

---

### Post by andiii on 2006-09-10
Had this thread existed before I tried KDE for a few hours I would have used that. ](*,)

---

### Post by meng on 2006-09-10
No problem, if you want to install everything that came with KDE (kubuntu-desktop) there's a link here:
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by andiii on 2006-09-10
I would be careful with pasting such large lists in my terminal. I will ave a closer look tonight, but amarok and k3b shall stay on my desktop.

---

### Post by meng on 2006-09-10
You can use the same syntax to remove a more limited list.

---

### Post by andiii on 2006-09-10
I know that, but does Norbert Newbie know it, too?

The author of that website should include some more informations or a warning or sth.

---

### Post by andiii on 2006-09-11
Just added .bin .jar and .run

---

