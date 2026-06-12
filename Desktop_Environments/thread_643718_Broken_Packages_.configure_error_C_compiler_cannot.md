---
title: "Broken Packages .configure: error: C compiler cannot create executables"
date: 2007-12-18
forum: Desktop Environments
---

### Post by jogel on 2007-12-18
Hello ,
I'm trying to ./Configure and this is my error
configure: error: C compiler cannot create executables

I tired to do apt-get update
also apt-get -f install

also apt-get install build-essential

this is the output 
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

I also tried doing Edit - -- > fix broken in synaptic.

Any suggestions ?

Thanks in advance ,

Jogel.

---

### Post by daou on 2007-12-18
Try ```
sudo apt-get install libc6-dev g++
```
It could also be a problem with your /etc/apt/sources.list
Post it if the previous command doesn't help.

---

### Post by danwood76 on 2007-12-18
Try enabling all the repositories and searching for g++ and libc-dev in synaptic.

What are you trying to compile?

regards,
Danny

---

### Post by jogel on 2007-12-18
when i try the command this is the output i get 

#apt-get install libc6-dev g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.5-0ubuntu14) but 2.7-3ubuntu1 is to be installed
E: Broken packages

I tried to ./configure EMBOSS

Thanks.

---

### Post by danwood76 on 2007-12-18
In synaptic click settings -> repositories and make sure every one of the repositories is enabled (except the CD).

Then click ok and reload (reload is very important here), then search for libc and select the libc6 and libc6-dev for install and click apply.

---

### Post by danwood76 on 2007-12-18
Also you should click the third party repositories and disable all of them, this will stop you from getting any broken packages.

---

### Post by jogel on 2007-12-20
> In synaptic click settings -> repositories and make sure every one of the repositories is enabled (except the CD).

Then click ok and reload (reload is very important here), then search for libc and select the libc6 and libc6-dev for install and click apply. 


I did what you mentioned 
Libc6 is colored green and you can only select remove. 
libc6-dev gives out the same error : 
lib6-dev
depends : libc6 (=2.5-0ubuntu14) but 2.7-3ubuntu1 is to be installed 

Please help :(

---

### Post by danwood76 on 2007-12-20
it sounds like you have installed a later version of libc than in the repositories, this would mean you cannot install the dev package as it wont be the correct version.

You will need to download and compile the 2.7 version yourself. I have 2.6 installed on mine which is the current version in the repositories.

---

### Post by PmDematagoda on 2007-12-20
Actually I think the OP's repositories may be incorrect, could you post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by jogel on 2008-01-09
Sorry for the long delay , 

Heres my Output :

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties
# deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all


Any ideas  ?

Thanks ,

Jogel.

---

### Post by PmDematagoda on 2008-01-09
Now could you post the result of:-
```
cat /etc/lsb-release
```

---

