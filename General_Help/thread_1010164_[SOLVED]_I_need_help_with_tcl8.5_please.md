---
title: "[SOLVED] I need help with tcl8.5 please"
date: 2008-12-13
forum: General Help
---

### Post by Bukiyu on 2008-12-13
hello guys first im a completely noob on ubuntu so I need someones help
I try to install amsn but i need tcl8.5 dependency I download tcl.85 and i try to install on terminal and i have try others things to but i cant if someone can help me to solve this please

---

### Post by taurus on 2008-12-13
There is an amsn available in the repos.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install amsn amsn-data
```

---

### Post by Bukiyu on 2008-12-13
ok i run the code on terminal now where i can see the amsn 
do I need to install it on Synaptic?
(yeah i know noobs question srry)

---

### Post by taurus on 2008-12-13
You can install it either from a terminal or with synaptic (or even with Add/Remove).  Once it's installed, it should be in Applications -> Internet.

---

### Post by Bukiyu on 2008-12-13
i have amsn version the one that use tcl8.4 do I need to uninstall that one??
btw: i cannot see amsn on add/remove -> internet
plus i download amsn package installer when i run this appear Error: dependency is not satisfiable: tlc8.5

---

### Post by taurus on 2008-12-13
You have not installed the amsn version that you downloaded so you can just delete it then.  By the way, it should be in Applications -> Internet once you installed amsn either from a terminal or with synaptic.

p.s.  Please do not double click the version of amsn that you've downloaded.  Instead, run those commands from a terminal to install the one from the repos.  It will take care of all the dependencies for you.

Again, there is an easy way (terminal--commands--or synaptic) to install it or there is a hard way (install it by hand) to install it.

---

### Post by Bukiyu on 2008-12-13
lool ok ok  
1) i have amsn under application internet but is the old version (taht i install before for synaptic using tlc8.4) 
2) i run the sudo apt-get update
sudo apt-get install amsn amsn-data u gave me and i get E: Couldn't find package amsn-data
3) the name of the package that i download is;
amsn_0.98svn10755+sapphire2.5svn36-0ubuntu1_i386.deb

sorry for the trouble is just that i dont wanna give up on this

---

### Post by taurus on 2008-12-13
The version from the repos (Intrepid) is 0.97.2.  So, if you want to install the newer version by hand, it's best to remove the one from the repos and then install tcl8.5 to satisfy the dependency.

Click System -> Administrations -> Synaptic Package Manager and in the Quick Search, type in **amsn**.  Click to remove it.  Then, from the Quick Search, type in **tcl** and you will be both tcl8.3 and tcl8.5.  Install tcl8.5 in your case then.  

Once it's done, close down synaptic and see if you can install your download version of amsn now.

---

### Post by albinootje on 2008-12-13
I just looked at the download-section of [http://amsn.sf.net/](http://amsn.sf.net/)
and they don't offer ubuntu packages it looks like.
They point to the package search of the ubuntu website instead.

But if you think that you can *really* trust the people where you downloaded
amsn_0.98svn10755+sapphire2.5svn36-0ubuntu1_i386.deb
from, then you can double-click on that file, and gDebi package-installer will try to resolve the dependencies for you.
This is however something you need to think about twice, and not make that routine behavior!

Also, since your installed Ubuntu release didn't know about amsn-data, then i assume (looking here [http://packages.ubuntu.com/search?keywords=amsn-data](http://packages.ubuntu.com/search?keywords=amsn-data)) that you're using Ubuntu Hardy or older.
Therefore it is quite possible that the installation will fail.

---

### Post by Bukiyu on 2008-12-13
well thats the problem i cant see tcl8.5 on synaptic i see 8.3 and 8.4 the tcl 8.4 is install, the problem is with the tcl8.5 
i have this tcl8.5_8.5.3-2.diff.gz, tcl8.5_8.5.3.orig.tar.gz 
i try to install them on terminal but i cant i dont know if i write the right command

---

### Post by taurus on 2008-12-13
Which release are you running?

---

### Post by Bukiyu on 2008-12-13
ubuntu 7.10

---

### Post by albinootje on 2008-12-13
You could upgrade to Hardy Heron.
Or try tcl8.5 from the gutsy-backports.

This page shows that tcl8.5 is in gutsy-backports :
[http://packages.ubuntu.com/search?keywords=tcl8.5](http://packages.ubuntu.com/search?keywords=tcl8.5)

---

### Post by Bukiyu on 2008-12-13
thnx both for the info i will try that and see im also updating ubuntu to 8.04 version too, so i let you know how its work

---

### Post by Bukiyu on 2008-12-14
ok i finally install amsn 0.98 but now a new error appear Error: Installing TLS module couldn't open socket host unreachable what do I have to do now ??

---

### Post by Bukiyu on 2008-12-14
never mind i fix the problem i download tcltls for synaptic and that fix the problem now i can use amsn

---

