---
title: "how can I install open office 2.0.3 in ubuntu 6"
date: 2006-07-07
forum: Desktop Environments
---

### Post by majeshps on 2006-07-07
How can I install openoffice 2.0.3 in Ubuntu 6.

---

### Post by FredB on 2006-07-07
> **majeshps said:**
> How can I install openoffice 2.0.3 in Ubuntu 6.

You'll have to wait until a backport is done. But let me ask you : is there any "killer" features added in 2.0.3 that you absolutely need ? ;)

---

### Post by majeshps on 2006-07-07
YAaap..Word hyperlink is not working properly in the other versions..but
 It is working perfectly in 2.0.3..

---

### Post by henriet on 2006-07-07
You can download the Rpm files from [http://www.openoffice.org/](http://www.openoffice.org/).
 Once you have extracted them from the tar.gz archive, go into the RPMs directory and enter:
```
fakeroot alien -d *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *debian*.deb
```

---

### Post by majeshps on 2006-07-07
I have tried the command ,but not working

---

### Post by henriet on 2006-07-07
What is the error message?

---

### Post by Joanie on 2006-07-16
> **henriet said:**
> You can download the Rpm files from [http://www.openoffice.org/](http://www.openoffice.org/).
 Once you have extracted them from the tar.gz archive, go into the RPMs directory and enter:
```
fakeroot alien -d *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *debian*.deb
```
Hey, this worked like a charm and saved me a lot of "figuring out" time!  Thanks so much!!

---

### Post by ccheaton on 2006-07-16
> **henriet said:**
> What is the error message?

For me, the error message is:

[FONT="Courier New"][SIZE="1"]ccheaton@host:~/downloads/OOo/OOC680_m7_native_packed-1_en-US.9044/RPMS$ fakeroot alien -d *.rpm
bash: fakeroot: command not found
ccheaton@host:~/downloads/OOo/OOC680_m7_native_packed-1_en-US.9044/RPMS$ sudo dpkg -i *.deb
Password:
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb[/SIZE][/FONT]

---

### Post by vigleik on 2006-07-16
> **ccheaton said:**
> 
bash: fakeroot: command not found


Maybe you have to install fakeroot first. Or you could probably type "sudo alien -d *.rpm" instead of "fakeroot alien -d *.rpm".

Vigleik

---

### Post by jgcamp99 on 2006-07-16
I have a feeling it will show up as an update in Synaptics Package Manager shortly ?

---

### Post by ccheaton on 2006-07-17
> **jgcamp99 said:**
> I have a feeling it will show up as an update in Synaptics Package Manager shortly ?

I hope so!  I wanted to try out Base for a project that I'm working on, but it doesn't even launch in my fresh Ubuntu installation...  ](*,)

---

### Post by ThrobbingBrain66 on 2006-07-17
> **henriet said:**
> You can download the Rpm files from [http://www.openoffice.org/](http://www.openoffice.org/).
 Once you have extracted them from the tar.gz archive, go into the RPMs directory and enter:
```
fakeroot alien -d *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *debian*.deb
```

this is great!  except for one error i get with the last command:

dpkg: regarding openoffice.org-debian-menus_2.0.3-2_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.0.3-2_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.0.3-2_all.deb

everything is installed, i just dont have my office menu anymore.

any ideas? thanks for the help!

---

### Post by ThrobbingBrain66 on 2006-07-17
i got it to work using

```
sudo dpkg --force-conflicts --force-overwrite --install *debian*.deb
```

---

### Post by amubu on 2006-10-05
trying to overwrite ...
, which is also in package openoffice.org-common x15 times at list.
please tell me how to remove this  openoffice.org-common.
synaptic says i have 2 broken packages. how can i find them and fix them? :-? 
please help

---

