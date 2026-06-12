---
title: "[SOLVED] Install/Uninstall"
date: 2006-06-13
forum: Desktop Environments
---

### Post by dstein on 2006-06-13
If I use apt-get to install a package, can I use aptitude to uninstall it or is it required that the same front-end be used to add/remove packages. Thanks.

---

### Post by 5-HT on 2006-06-13
Yes, you can use aptitude to uninstall package that has been installed using apt-get. 
However, you will not be taking advantage of aptitude's unused-dependency handling unless you manually edit the automatic/manual flags for the package's dependencies.

If the package you want to remove is not a dependency of any installed package, a neat trick can be to mark the package you want removed as installed 'automatically' by aptitude. The next time you fire up aptitude, it'll want to remove that package and all of its unused-dependencies.

---

### Post by dstein on 2006-06-13
How would I mark it as "installed 'automatically' by aptitude"

---

### Post by dstein on 2006-06-13
I also meant to ask, why are some packages not available for install/uninstall with Ubuntu's Add/Remove application? And also, do all the package management programs access the same repositories listing? Thanks.

---

### Post by 5-HT on 2006-06-14
[quote=dstein]How would I mark it as "installed 'automatically' by aptitude"[/quote] 
To set the 'automatically installed' flag for a package*:

```
 sudo aptitude markauto <package> 
``` 
To set the 'manually installed' flag for a package*:

```
 sudo aptitude unmarkauto <package> 
``` 
*Only use the package's name, not the < & >

You can also do the same thing from the text-based-GUI by going to the "package" menu (or by using the keystroke mentioned in the menu) and selecting the appropriate option.

The manual for Aptitude can be found in /usr/share/aptitude/README.
I would highly suggest that you read it to become comfortable with the program (there are a lot of options in Aptitude that can save you a lot of time if you know how to use them).

[quote=dstein]I also meant to ask, why are some packages not available for install/uninstall with Ubuntu's Add/Remove application? And also, do all the package management programs access the same repositories listing? Thanks. [/quote] 
The Add/Remove Applications utility is a simplified, easy-to-use front-end to Synaptic, which is a front-end to apt-get (aptitude is also a front-end to apt-get) which is a front end to dpkg (that's a lot of front-ends isn't it?).

Add/Remove Applications, IMO, is geared more towards being noob/new-user friendly as it'll only list a few different packages for any given function. If you click on the 'advanced' option in add/remove applications, you'll be presented with Synaptic.

All the package managers do hit the same repositories, it's just that Add/Remove Applications only lists a subset of all the available packages (my guess is to make it less confusing/intimidating for new users).

Hope that helps.

---

### Post by dstein on 2006-06-14
Thanks for the thorough response. I am going to begin reading the Aptitude Manual.

---

### Post by dstein on 2007-12-31
I am starting to use Ubuntu more frequently and I would like to take the time to really learn one of the package managers. Should I take the time to learn apt-get, aptitude, or synaptic? Thanks!!!

---

### Post by PeterJS on 2007-12-31
There really only is one package manager, apt/dpkg, everything else is just fluff. Apt-get and aptitude work in essentially the same way, the major difference being that aptitude is smarter and better automates handling dependencies on removal. And each tool is better suited to some jobs than others, apt-get/aptitude is great if you know exactly what you want, or are planning to post a complex set of package installs in a text forum. Synaptic, in my experience, is best for finding things that you know some keywords for but not the name, note this could be done with the commandline tools as well (apt-search), but synaptic is all point and click and makes multiple searches and installing from search results easy. So there is no one best tool for all situations. If you want to learn how things work, read up on apt-get, but do so with the understanding that there are other applications built around apt-get that use the same underlying framework and libraries to do more.

---

### Post by dstein on 2008-02-08
I have two last questions about aptitude. If I install something with Aptitude, should I use aptitude to upgrade it later, or will Ubuntu Update Manage update it as well? I run the Update Manager by clicking System -> Administration -> Update Manager.

Lastly, I just used Aptitude to install emacs, and it asked me to insert my Ubuntu CD. Fortunately, I had it. I typed 'sudo aptitude install emacs'. Any idea why I was required to insert my CD. I did not have to do this the other day when installing emacs with apt-get. Any way to avoid this? Thanks.

---

### Post by PeterJS on 2008-02-09
All of the apt front ends feed in to the same database, so any thing installed with one (aptitude) will show up in another (update manager). For the CD being needed to install emacs, in System > administration > software sources, and check on the the front and third party tab to see if there is a cd-rom entry enabled on either one.

---

### Post by dstein on 2008-02-09
Thanks PeterJS. I have two final questions. First, if I install software with aptitude, do the other front ends keep track of the dependencies. More specifically, if I install program A with aptitude, which happens to also install program B, then I switch to syna[tic... If I remove A with synaptic, will it know to also remove B?

Lastly, I am not clear how suggested packages are handled. Suppose package A suggests package B. If I install package A, will be be installed? Is there anyway to change these settings? Thanks.

---

### Post by PeterJS on 2008-02-09
> **dstein said:**
> Thanks PeterJS. I have two final questions. First, if I install software with aptitude, do the other front ends keep track of the dependencies. More specifically, if I install program A with aptitude, which happens to also install program B, then I switch to syna[tic... If I remove A with synaptic, will it know to also remove B?

Lastly, I am not clear how suggested packages are handled. Suppose package A suggests package B. If I install package A, will be be installed? Is there anyway to change these settings? Thanks.

The answer to both is that each front end does things a little differently, apt-get really only knows the bare minimum, it gives you the option of uninstalling automatically installed packages, but won't mark packages as auto installed, while aptitude does. Update manager doesn't care about automatically installed dependencies, or manually installed apps, it just updates anything it finds installed. Synaptic will mark packages as automatically installed, but won't removed them automatically, but will list them all in one place making them easy to remove.

For suggested packages, apt-get will list them, but they scroll by so fast I don't think anybody can or does actually read them. Synaptic has them listed as options to install them from the context menu of the package that suggests them. I think aptitude does something really funky like install them as dependencies, but don't hold me to that I don't usually use aptitude.

---

### Post by dstein on 2008-02-11
I guess I have two final questions about the software packages. First, what is the difference between purging and deleting. I tried reading up on it but I am not sure I fully understand. Lastly, when in Aptitude or any other package managers, how can I see where programs will be installed to? For example, if I want to install package A, how can I see which directories or where on my system it will be? Also, is there any way to do this for programs that have been installed. Thanks.

---

