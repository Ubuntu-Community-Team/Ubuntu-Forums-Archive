---
title: "MySQL source package"
date: 2009-01-23
forum: General Help
---

### Post by reeksy on 2009-01-23
Hi

I want to install MySQL from source however i don't know which package to download from [their downloads page](http://dev.mysql.com/downloads/mysql/5.1.html#linux)!

I have the 32 bit version of Ubuntu installed.

reeksy.

---

### Post by Titan8990 on 2009-01-23
x86 =  32bit


Any particular reason you are compiling from source? Do you know about the issues with uninstalling and upgrading programs that were compiled from source?

---

### Post by reeksy on 2009-01-23
Great thanks.

> **Titan8990 said:**
> Any particular reason you are compiling from source? Do you know about the issues with uninstalling and upgrading programs that were compiled from source?


Because all the devs i work with know how to create a LAMP install from source...and i've never complied anything from source! So i thought it was about time i learnt.

What's the issues with upgrading packages that have been installed from source?

Thanks again,
reeksy

---

### Post by mb_webguy on 2009-01-23
> **reeksy said:**
> What's the issues with upgrading packages that have been installed from source?

Well, for starters, a new version of an application may have newer dependencies than what you have currently installed, which means you would have to first meet those dependencies.  Which may mean compiling them from source.  Which may mean you have to first meet their dependencies.  Which may mean compiling them from source.  Which may mean...  (Welcome to dependency hell.)  And of course, since some other applications may depend specifically on the older packages, you may end up breaking those other applications.  And unless you use checkinstall when compiling all of that software, downgrading to previous versions of the software can be tedious.

Basically, there's really no reason to compile software from source if there are absolutely no other options available.

---

### Post by reeksy on 2009-01-23
Ah, i see!

Incidentally, i've downloaded the Linux (x86) (non RPM package) but after extracting it, there isnt a configure file! Is that normal? Installing Apache from source was a breeze, MySQL isnt so easy!

How can i make and make install without configuring the package first!?

reeksy

---

### Post by reeksy on 2009-01-23
Whoops! I downloaded a binary package not the source package! Problem solved.

---

