---
title: "Is apt-get powerful ???"
date: 2006-07-17
forum: Desktop Environments
---

### Post by ss0007 on 2006-07-17
Hi , 
i am wondering if apt-get can simplify compiling tarballs from source . Since apt-get can fetch source files from repos, 
can it automatically find dependencies when compiling and fix them 
as it finds and install to system ?

if this is possible ,can someone post the command to execute it ?


Thx very much in advance.

---

### Post by mcduck on 2006-07-17
I remeber it workin with a command 'sudo apt-get buid-dep packagename' or something like that. Why don't you just 'man apt-get' to check the correct syntax?

---

### Post by ss0007 on 2006-07-17
hmmm ... ok .. thx  ..
but is thr anyway for exact(or advanced) command pattern to solve this guys ..
sorry , i hate reading man pages !!!

...
TIA

---

### Post by mogliii on 2006-07-17
Hi,

There is a program called auto-apt.

Its in some repository. Dont know if main or universe.

When you do
```
auto-apt run ./configure
```
it will halt the process if something is missing, install, and then continue. But I havent used it a lot so I am not sure how well it works.

Also I find in my notes:
```
apt-get build-dep *
```
But I'm not sure what it means. * is maybe the thing you want to compile. But not sure which file exactly you have to point at. 

Does anyone have some experience with it?

---

### Post by christhemonkey on 2006-07-17
apt can get the source, and all the necessary dependencies.
But the actual compiling can still be left to you.
```
sudo apt-get build-dep programA
sudo apt-get source --download-only programA 
```
This will just donwload it.

Change the last line to this if you want to compile it automatically as well:
```
sudo apt-get source --compile programA 
```

---

### Post by ss0007 on 2006-07-17
hey thx for all ur replies.
that answered my question .

Hope if someone can bring up a How To's in the compiling of source tarballs for new users, it would be grateful. Being a newbie, i found such difficult to compile the src and scared not to download the latest stuffs , 

I hope, if these kind of simple compile methods are exposed in How Tos' evry newbie can njoy with linux .

---

### Post by asplode on 2006-07-17
I know it seems scary, but most programs can be compiled and installed by simply unzipping the tarball and 3 simple commands.
```
tar -xvf *filename*.tar.gz
cd *filename*
sudo apt-get build-dep *program-name*
./configure
make
sudo make install
```

Sometimes you might want to view the README or INSTALL file for hints or tips on installing, and for whether or not it is compiled in the (standard) method or not.  Thats as simple as changing to the directory and typing
```
view README
```
or```
view INSTALL
```
and CTRL + Z to exit vi.

---

