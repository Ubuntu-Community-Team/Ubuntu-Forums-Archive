---
title: "Search Peculiarities"
date: 2013-09-03
forum: Desktop Environments
---

### Post by Cos_Marchy on 2013-09-03
Hi,

I'm struggling with searching in Ubuntu 12.04 LTS using the inbuilt file manager.

I am searching for a file called python.h and I know where it should be (usr/lib/python2.7/).

When I search the root for this file it it found.  When I check the properties of the file, it says the location is where I thought it would be.  So far so good...

But, if I go to usr/lib/python2.7/ directory and manually try and find any .h file they are not listed.  

However, if I search root for all .h files nothing is found but if I search for a specific .h file it is found.

I need to find all of the .h files in this location because when I copied this folder, they were all missing in the destination folder.:confused:  I only copied and pasted!!

Can anyone shed any light on this please?

Thanks

---

### Post by steeldriver on 2013-09-03
Hello and welcome to the forum

Header (.h) files would usually go in /usr/include/ not /usr/lib (although there are some python dist-packages headers in /usr/lib). If you tell us exactly what package you are trying to install perhaps someone can give you specific advice on where the files should go.

As to why a search from / is not finding the file, if you have installed it recently then it may be that the locate database has not yet been updated (it's usually only updated automatically once a day) - if so, you can run

```
sudo updatedb
```

and then try searching again. Alternatively, you can use the command-line 'find' command which is slower but doesn't rely on the database, e.g.

```
find /usr -name 'python.h'
```

---

### Post by Cos_Marchy on 2013-09-03
> **steeldriver said:**
> Hello and welcome to the forum

Header (.h) files would usually go in /usr/include/ not /usr/lib (although there are some python dist-packages headers in /usr/lib). If you tell us exactly what package you are trying to install perhaps someone can give you specific advice on where the files should go.

As to why a search from / is not finding the file, if you have installed it recently then it may be that the locate database has not yet been updated (it's usually only updated automatically once a day) - if so, you can run

```
sudo updatedb
```

and then try searching again. Alternatively, you can use the command-line 'find' command which is slower but doesn't rely on the database, e.g.

```
find /usr -name 'python.h'
```

Hi steeldriver, thanks very much for your reply :)

I'm not trying to install anything rather take a copy of the python2.7 directory so I can try to compile some source (firstly I'm not sure how you alter the makefiles to point to the right directories and secondly it's probabily safet to move the directory to where the makefile thinks it is in case anything goes pair shaped with the originals :wink:)

I tried  ```
sudo updatedb
``` but this hasn't made ay difference at all.  

Is there anything else which effects search?  

Thanks

---

### Post by steeldriver on 2013-09-03
Are you sure the file you want is not called Python.h? Remember *nix is case sensitive.

---

### Post by Cos_Marchy on 2013-09-04
I tried searching for 'Python.h' and python.h' but I got the same results - it did manage to find it regardless of case.

In the end I resorted to using the cp in the terminal which seemed to copy every file.  

A little frustrating the gui doesn't work :(

---

