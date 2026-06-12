---
title: "Q: Installing Cedega 5.1 on Dapper(6,06)"
date: 2007-01-15
forum: Gaming &amp; Leisure
---

### Post by 2g4u on 2007-01-15
Hi there,

First I wanna say sry if my first post isn't in the right section.

I have problem installing Cedega on Ubuntu 6.06. I have cedega_5.1_i386.deb installer package. I tried to use Gdebi Package Installer to install it, but it gives me an error: Dependency is not satisfiable:xlibs. Then I tried to updete xlibs package with Synaptic Package Manager(I wonder if xlibs-dev is the same as xlibs), but it seems it dont have a newer version aviable(my ver is 7.0.0). So could some1 give me a "noobie" guide on how to install Cedega ?

---

### Post by DARKGuy on 2007-01-15
Have you tried running a terminal then typing:

sudo dpkg -i cedega_5.1_i386.deb 

That (and if you have the full repositories) should solve the dependency problem too, since dpkg does something like apt-get. If it says stuff about not being able to find a dependency, then just use "apt-cache search xxxx" (where xxxx are just 2-3 characters of the full name) and press TAB twice, that will show you a list of package names starting with those characters. If nothing relevant is shown, you've got to update your repositories, else, just "apt-get install package" and you're done.

By the way, no, xlibs-dev isn't the same as xlibs, the -dev means it's a development version, intended only if you want to compile stuff that uses xlibs :P

---

### Post by Perfect Storm on 2007-01-15
Go to Transgaming.com. Login and download the latest version of Cedega. That should solve the problem.

Closing due to piracy.

---

