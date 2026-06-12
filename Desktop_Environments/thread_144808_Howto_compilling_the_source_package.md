---
title: "Howto compilling the source package?"
date: 2006-03-15
forum: Desktop Environments
---

### Post by mzkapoo on 2006-03-15
I'd like to know howto compilling, step by step, the source package that I have downloaded from the vendor website such as OpenOffice.org 2.0.2.

I'd like you to tell me about howto parses them to *.deb too.

Please......

I'm a newbie linux.

---

### Post by Gustav on 2006-03-15
First untar the package:
```
tar xvfz <package_name>
```
then go to the new directory:
```
cd <new_directory_mostly_named_package_name>
```
then do the following steps to compile it:
```
./configure
make
```
then make a .deb of it:
```
checkinstall
```
then install the .deb:
```
dpkg -i <package_name>.deb
```

To do this you need to have the packages build-essential and checkinstall installed, they are availible via synaptic or apt.

---

### Post by mzkapoo on 2006-03-15
Thank you so much, Sir.

---

### Post by Sef on 2006-03-15
Before compiling, you need to have downloaded build-essentials, otherwise you can't compile.

sudo agt-get install build-essentials

---

### Post by Ramses de Norre on 2006-03-15
Take a very deep look at the output of ./configure, things like missing dependencies are in it. Everything needs to be ok, if not install the dependencies, needed compilers etc untill ./configure says that everything is fine.
Going further without doing this wont work.

---

### Post by engla on 2006-03-15
This command automatically fetches "build dependencies" for *the package version that is in the repositories*. If the versions are close, it mostly works anyway...

```
sudo apt-get build-dep openoffice.org2
```

However, trying that yields 104 packages / 80M, and I thought I already had many -dev packages installed!
So either you can get away quite a lot cheaper (less packages), or this is not a very fun compile.

Indeed, if you don't know the basics of compiling packages, I don't recommend you to try to build this beast.

---

