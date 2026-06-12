---
title: "problem conpiling cpp file"
date: 2009-05-16
forum: General Help
---

### Post by muctadir on 2009-05-16
i have to compile a c++ file. so, i tried g++ -o output input.cpp. it requires g++ to be installed. so i tried sudo apt-get install g++........

it did not worked. it says =
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++: Depends: cpp (>= 4:4.3.3-1ubuntu1) but 4:4.3.1-1ubuntu2 is to be installed
       Depends: gcc (>= 4:4.3.3-1ubuntu1) but 4:4.3.1-1ubuntu2 is to be installed
       Depends: g++-4.3 (>= 4.3.3-1) but it is not going to be installed
       Depends: gcc-4.3 (>= 4.3.3-1) but 4.3.2-1ubuntu12 is to be installed
E: Broken packages

please help........

---

### Post by muctadir on 2009-05-16
i need help.......
pls help me...

---

### Post by Pidgin on 2009-05-16
It seems that g++ is newer than the packages it depends. There may be problems in your /etc/apt/sources.list. Please post the content of that file as well as files in /etc/apt/sources.list.d/, if any.

---

### Post by issih on 2009-05-16
Try installing the package "build essential", the fact that you can't install g++ alone isn't right, and you might well have something fishy in your sources, but hat package is the one most people use to get hold of common compilers and software libraries.

Hope that helps

---

### Post by Pidgin on 2009-05-16
> **issih said:**
> Try installing the package "build essential", the fact that you can't install g++ alone isn't right, and you might well have something fishy in your sources, but hat package is the one most people use to get hold of common compilers and software libraries.
Hope that helps
Agree.

---

