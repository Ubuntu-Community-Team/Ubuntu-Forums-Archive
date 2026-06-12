---
title: "Programming"
date: 2009-03-25
forum: General Help
---

### Post by RedSingularity on 2009-03-25
Anyone know of good programming software for linux?  In class i am learning VB and c++.  Are there any similar programs that will work on ubuntu?  I currently run VB in my Vista virtual install but i would like to write programs in ubuntu.  

Thanks

---

### Post by DGortze380 on 2009-03-25
> **Shadow121 said:**
> Anyone know of good programming software for linux?  In class i am learning VB and c++.  Are there any similar programs that will work on ubuntu?  I currently run VB in my Vista virtual install but i would like to write programs in ubuntu.  

Thanks

gcc is the c++ compiler for most UNIX based systems.
open a terminal and type 'man gcc' (without the quotes) for more info.

typical usage for a beginner: gcc inFile.cpp -o outFile


I'm sure there is a VB compiler available, but you won't necessarily have full functionality of .NET, I wuld use Visual Studio in Windows for VB.

---

### Post by cholericfun on 2009-03-25
you could also get intels icc (free for single users), in case that is what you learn to use.
fortran (gfortran in the reopos or again ifort) is another programing language,
and of course theres 1000s of other languages out there, you WILL find compilers for all of them really.

---

### Post by lovinglinux on 2009-03-25
> **cholericfun said:**
> ...
very very stupid question of my own, i'm trying to open a new thread
but cant find where to ?
a quick reply would be much appreciated!
thanks

Click the breadcrumb in the top of the page to access the forum page and the "New Reply" button will become "New Thread".

---

### Post by mb_webguy on 2009-03-25
If you're looking for an IDE like Visual Studio, you might want to look into:
[LIST]
[*]Code::Blocks (C++)
[*]MonoDevelop (C, C++, C#, Java, Visual Basic.NET, Boo, Nemerle, and CIL)
[*]KDevelop (Ada, Bash, C, C++, Fortran, Java, Pascal, Perl, PHP, Python and Ruby)
[*]NetBeans (C, C++, Java, JavaScript, PHP, Python, Ruby, and Groovy).
[/LIST]

Note that there are no IDEs for Visual Basic 6 for Linux, since VB6 is a Microsoft proprietory language, so any such IDE would require a license from Microsoft.  VB.NET is a bit more available, but MonoDevelop is one of only a handful of IDEs for Linux that supports it.

---

