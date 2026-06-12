---
title: "Error installing Matlab 2009b on Ubuntu 12.04"
date: 2012-08-29
forum: Education &amp; Science
---

### Post by loremaster on 2012-08-29
Hey guys,  i got a problem installing matlab which i hope i can get help for.

Using Furious ISO Mount, i was able to mount 2009b iso and run the install file. 

The start of the installation is smooth as well until i get to the stage where the installation prompts for space to install matlab and i get this error for lack of installation space.



However i checked my harddisk space and it says there are sufficient space on/dev/sda5.

I submitted 2 ss of the error and the hard disk space i have!

I can't made sense of this error and how to ressolve it plus i am new to ubuntu so would really appreciate any help. Thanks!

---

### Post by PC_load_letter on 2012-08-30
Did you run the installation script with super user permissions? 
Let's say that the installation script is called 'install', in such case, you type the following in a terminal:
```
sudo install
```

---

### Post by loremaster on 2012-09-02
I found the problem, apparently i redirected the installation of the root folder to the iso file itself therefore it could not installed. I created a new folder and pointed the installation to it so i could install the matlab 2009b.

I got a new problem now though, i am trying to install gcc 4.2 on matlab 2009b since it works with it only and gcc 4.6 or 4.7 doesn't. 

I tried using 

sudo aptitude install gcc-4.2-multilib libstdc++6-4.2-dev


but it keeps saying can't find the package finding the description.


I have already added 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main to the end of my sources.list but aptitude gives me that error when i try to install gcc 4.2.

Must i download the package first for aptitude to install or aptitude finds it on my behalf?

Any help is appreciated! Once again thanks!

---

