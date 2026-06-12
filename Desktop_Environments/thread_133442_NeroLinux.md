---
title: "NeroLinux"
date: 2006-02-20
forum: Desktop Environments
---

### Post by Digidiz on 2006-02-20
i am trying to install neroLinux, after successfully installing alien to convert the rpm package to tgz file format, i also successfully extracted the files to the /opt/Nero/

i have tried using sudo apt-get install command, but this is not installing the program. can anyone tell me where i am going wrong??

---

### Post by codejunkie on 2006-02-20
[QUOTE=Digidiz]i am trying to install neroLinux, after successfully installing alien to convert the rpm package to tgz file format, i also successfully extracted the files to the /opt/Nero/

i have tried using sudo apt-get install command, but this is not installing the program. can anyone tell me where i am going wrong??[/QUOTE]
you could just download the .deb package from ftp.nero.com and install it.

---

### Post by Digidiz on 2006-02-20
is that using the synaptic manager??

---

### Post by gibson on 2006-02-20
If you goto nero and download nerolinux it gives you the choice of rmp or deb.

Download the deb then, 

> dpkg -i thefileidownloaded.deb

hope this helps

---

### Post by Beej on 2006-02-20
Digidiz, 
download the .deb to you home folder. Open the terminal and type

sudo dpkg -i nameofpackage

Where "nameofpackage" is the filename of the package including the.deb file extension. This should install Nero for you. 
I don't use Nero myself so I can't be sure, but you may get error messages due to unmet dependancies. If you do get these, search for these files in synaptic or use 

sudo apt-get install packagename

from the terminal, then repeat the first step.

If you don't need Nero for any particular purpose, I would recommend K3B as an excellent alternative, its in the repos, just search in synaptic.

Beej.

---

### Post by Digidiz on 2006-02-20
as i said i tried the sudo apt-get install packagename, this is easily done by typing the first few letters of the packagename, then hitting TAB

---

### Post by Beej on 2006-02-20
Digidiz, I'm not with you. Have you tried **"sudo dpkg -i packagename"** from the directory the .deb is in?

---

### Post by Elvish Legion on 2006-02-20
[QUOTE=Digidiz]as i said i tried the sudo apt-get install packagename, this is easily done by typing the first few letters of the packagename, then hitting TAB[/QUOTE]


Why are you using apt-get? I don't remember nero being in the repo, therefore you have to download it and use the dpkg -i command

---

### Post by Digidiz on 2006-02-20
not the dpkg -i option but u mentioned the sudo apt-get install option of which i have already tried

---

### Post by larsemil on 2006-02-20
[QUOTE=Digidiz]not the dpkg -i option but u mentioned the sudo apt-get install option of which i have already tried[/QUOTE]


well that was for installing the packages needed by nero. not neroitself.

so once again.

**1. go to neros homepage and download the debian package(.deb)**

**2. dpkg -i thefileyoujustdownloaded.deb**

now it should be working.

if**(and only IF)**, dpkg -i gives some dependencieerrors then you should 
sudo apt-get install thefilesneededbynero

---

### Post by Digidiz on 2006-02-20
did that and all it gave me was this

Selecting previously deselected package nerolinux.
(Reading database ... 82830 files and directories currently installed.)
Unpacking nerolinux (from nerolinux-2.0.0.5-x86.deb) ...
Setting up nerolinux (2.0.0.5-1) ...
Operating System: Debian GNU/Linux version testing/unstable

---

### Post by Digidiz on 2006-02-20
strange after a while it was there, lol cheers

---

### Post by gibson on 2006-02-20
[QUOTE=Digidiz]did that and all it gave me was this

Selecting previously deselected package nerolinux.
(Reading database ... 82830 files and directories currently installed.)
Unpacking nerolinux (from nerolinux-2.0.0.5-x86.deb) ...
Setting up nerolinux (2.0.0.5-1) ...
Operating System: Debian GNU/Linux version testing/unstable[/QUOTE]


Now goto a terminal.... type nero and press TAB.

it should bring up some options... choose the executable and press enter...

---

### Post by gibson on 2006-02-20
hehe oops

we must have been replying at the same time

never mind

---

### Post by vishinator on 2008-04-09
mine says soemthing about being a superuser but i am admin

---

