---
title: "please help !! problem installing programs"
date: 2006-09-22
forum: Desktop Environments
---

### Post by stormie on 2006-09-22
i cant figure out how you are spposed to intall programs idownloaded a linux program and cant figure out how to installit please help me
thanks

---

### Post by arkangel on 2006-09-22
which program? 

if you are new to linux,  the odds are with you , the program is most probably in a repository and  you can get it via synaptic 

System>>Administration>>synaptic 
and do a search  , this will install the program and all dependencies for you 
there is a [guide]("http://ubuntuguide.org/wiki/Dapper") point 19.22

---

### Post by mcman42 on 2006-09-22
Usually most software that you download comes with either "readme" or "install" text file that has instructions for installing it. The tupical way would be:
1. cd to the folder with extracted files
2. "configure"
3. "sudo make"

But ofcourse the most easiest and convenient way is the one that previous poster described.

---

### Post by stormie on 2006-09-22
well i ha ubuntu on one computer but my internet software  doesnt support linux so i have to use the other comp tat is running windows xp to download programs copy them to my flash drive then i can transfer them the other comp but i was trying to install the f-prot antivirus and i cant figure out how to get it to install
but is here a way to pull up the repository on the internet under windows?
thanks

---

### Post by arkangel on 2006-09-22
I saw the  Fprot web page it comes in 3 flavours rpm , deb and tar.gz
rpm is for  redhat and  madriva (and kids), deb is for all debian based (ubuntu is one of these)  and the other is the generic  that should work in any linux distro

the easiest way to install is to use the  deb 

open a terminal  and go to the directory where the file is 
# cd [where/my file/is]
# sudo dpkg -i [filei wanttoinstall].deb

if you download the rpm you have to convert it into a debian one, for that you need alien  (if your computer have no internet then there is a problem if alien is not installed  )
just for ur info:
#cd [where/my file rpm /is]
#fakeroot alien -d [myfile].rpm
#sudo dpkg -i [filei wanttoinstall].deb


whenever you need a program , try to get the deb  version and isntall it using dpkg (dedian pakage manager)
one question ,  why do you need an antivirus under  linux ?

---

### Post by Delkster on 2006-09-22
If it's a deb package, you might be able to just double-click on it and the package installer called GDebi should handle it for you. However, ff the package hasn't been made specifically for Ubuntu, there may be some problems, for example with its dependencies on other packages.

---

### Post by stormie on 2006-09-22
ok ill try that 
thanks guys
stormie

---

### Post by Omnios on 2006-09-22
Link on installing stuff

[http://ubuntuforums.org/showthread.php?t=171822](http://ubuntuforums.org/showthread.php?t=171822)

---

