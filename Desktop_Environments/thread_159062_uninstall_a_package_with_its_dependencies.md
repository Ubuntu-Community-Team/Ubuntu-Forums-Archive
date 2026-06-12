---
title: "uninstall a package with its dependencies?"
date: 2006-04-12
forum: Desktop Environments
---

### Post by louis_nichols on 2006-04-12
Hi! here's what I'm thinking:

I'd like to be able te remove a package and all other packages it depends on, that aren't needed (of course) by others. Cuz i keep trying this and that, installing packages with their dependencies, and then I unistall stuff, but leave the dependencies, and I bet there are tons of libs on my system that aren't needed anymore.

Does anyone know a command for this?

---

### Post by dermotti on 2006-04-12
I would be interested in this as well.

So far the way i have been doing it is looking through my synaptic history and removing the dependencies manually.

---

### Post by aysiu on 2006-04-12
I believe if you install a package using *aptitude* instead of *apt-get*, the dependencies will be remembered, so that you can uninstall them along with the package (using *aptitude remove*, of course).

Barring that, you can install *deborphan*, which, I believe, finds packages that no other packages depend on.

---

### Post by louis_nichols on 2006-04-12
thanx for the reply aysiu! I'll give them both a try.

---

### Post by 5-HT on 2006-04-12
[quote=louis_nichols]thanx for the reply aysiu! I'll give them both a try.[/quote]

Aptitude's great. The only cach is that you have to install the package with aptitude in order for any unused dependencies installed with it to get automatically removed when the package is uninstalled.

There is a trick around this though, you can manually mark packages as 'automatically installed'. If any package marked as 'automatically installed' is no longer needed by anything else, it'll be removed automatically the next time you do anything with aptitude. You can get packages marked like this either from aptitude's GUI interface, or just from the CLI.

HTH

---

### Post by louis_nichols on 2006-04-12
So let me see if I get this right: I use *$sudo aptitude install packagex* and it will install the paqckage and all its dependencies, and then use *$sudo aptitud euninstall packagex* and it will automatically uninstall the package + unneeded dependencies?

---

### Post by 5-HT on 2006-04-12
[quote=louis_nichols]So let me see if I get this right: I use *$sudo aptitude install packagex* and it will install the paqckage and all its dependencies, and then use *$sudo aptitud euninstall packagex* and it will automatically uninstall the package + unneeded dependencies?[/quote] 
Yup.  Any unneeded dependencies of the program you are removing will go along with it. 

One little modification though:

The syntax for removing packages is ```
 sudo aptitude remove <package> 
``` or to also remove config files you could do a ```
 sudo aptitude purge <package> 
``` 

Aptitude also has a GUI interface, just enter 'sudo aptitude'.

Aptitude's options and syntax from the CLI are pretty much the same as for apt-get.

There are a few little differences though. To read the manual type 'man aptitude'.

There is also a great guide available in the help menu in GUI mode.

HTH

---

