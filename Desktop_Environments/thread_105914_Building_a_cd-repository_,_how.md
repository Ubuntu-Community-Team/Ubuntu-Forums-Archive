---
title: "Building a cd-repository , how ?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by Ultimo Aliento on 2005-12-19
Hi !

I have installed ubuntu to many friends, but they have a 56k conection... so many of the programas, codecs, plug-ins for mozilla and other stuff, are beyond his posibilities.

I want to know if i could create a cd, with all the stuff they need to get ubuntu working with anything, and how i could create that ?

And, if i can create the cd, i can use aptitude to config the packages in the repository cd?

---

### Post by towsonu2003 on 2005-12-19
I did that CD repository thing once and it's a little bit of torture. For some reason I can't remember how I did it :)

This link may be a good starter: [http://www.ubuntuforums.org/showthread.php?t=7455&page=2&highlight=local+repository](http://www.ubuntuforums.org/showthread.php?t=7455&page=2&highlight=local+repository)

/edit/ okay now I remember a little bit doing it my way (probably longer): 

1.packages.ubuntu.com -> you will need this to get packages and dependencies of them. for each package, check to see if the other computer has dependencies installed. 
2. create a local folder ~/localfolder and download files in here
3. follow this [http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862) for making ~/localfolder a repo
4. burn ~/localfolder to cd
5. on other computer, sudo apt-cdrom add then put cdrom in. you should now have the repo. be very careful with dependencies reported by apt-get / synaptic as to not break system... u MUST have all dependencies for all files you will install (including dependencies of dependencies as well) in that CDROM unless the dependency is installed in computer. 

hopefully this will help...

---

### Post by Ultimo Aliento on 2005-12-19
Thanks ! , i will try to do this, along this week :D

---

### Post by az on 2005-12-19
A simple way to do it:

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

Install ubuntu on a machine and then install all the stuff you want using apt.  You know you have all the dependancies that way.  The you make a repository cd out of your downloaded debs.

---

### Post by towsonu2003 on 2005-12-20
[QUOTE=azz]A simple way to do it:

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

Install ubuntu on a machine and then install all the stuff you want using apt.  You know you have all the dependancies that way.  The you make a repository cd out of your downloaded debs.[/QUOTE]

I think this howto assumes that ubuntu was freshly (i.e. no tweaks at all after install) installed on the first machine (the one which can download using apt-get). am I correct? if so, when OP tries this on own machine, s/he may have trouble with dependencies?

Disclaimer: I am in no way saying that my way is better, because my way sucks... ;)

---

### Post by az on 2005-12-20
[QUOTE=towsonu2003]I think this howto assumes that ubuntu was freshly (i.e. no tweaks at all after install) installed on the first machine (the one which can download using apt-get). am I correct? if so, when OP tries this on own machine, s/he may have trouble with dependencies?
[/QUOTE]

Yes, that it correct.

---

### Post by Strannik on 2005-12-20
I used the following script in an empty directory to gather all the packages that I have installed in it:

#!//bin/sh
dpkg --get-selections | grep -v "deinstall" | awk '{print $1}' | xargs dpkg-repack

ps. make sure that you have dpkg-repack installed before, if not, sudo apt-get install dpkg-repack. Will take a while, but it will give you all the .deb packages fresh and clean. =)

---

### Post by towsonu2003 on 2005-12-20
[QUOTE=Strannik]I used the following script in an empty directory to gather all the packages that I have installed in it:

#!//bin/sh
dpkg --get-selections | grep -v "deinstall" | awk '{print $1}' | xargs dpkg-repack

ps. make sure that you have dpkg-repack installed before, if not, sudo apt-get install dpkg-repack. Will take a while, but it will give you all the .deb packages fresh and clean. =)[/QUOTE]

don't want to sound like a retard but, what's the 'english' of that string of letters? ;0

---

### Post by az on 2005-12-20
dpkg --get-selections 
print out the list of installed and removed packages


grep -v "deinstall" 

Get rid of the deinstalled ones


awk '{print $1}' 

Strip off everything other than the first part - you just get the package name.


xargs dpkg-repack

Run that through dpkg-repack which repackages installed packages into the deb file.



You will end up with all of the extra packages along with the ones you already have on the cd.

---

### Post by towsonu2003 on 2005-12-20
wow... simply amazing...

---

### Post by anil_robo on 2005-12-21
Could someone compile all the info from this thread to write a single, concise, newbie-friendly how-to? I want to build some CD repositories from [www.sourceforge.net](www.sourceforge.net). THanks! :)

---

