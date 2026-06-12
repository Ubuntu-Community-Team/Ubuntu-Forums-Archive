---
title: "IF i install any packages i get...."
date: 2005-08-23
forum: Desktop Environments
---

### Post by c0rderr0y on 2005-08-23
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
XXXXX : Depends: XXXXX (= 3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed
E: Broken packages

replace X with what you like   ](*,)

---

### Post by Juergen on 2005-08-23
As you can see, the package you want to install needs the exact version of another package from Ubuntu (= 3.0.10-1ubuntu3) but you have a newer version.

Mostly the dependencies are not '=', but '>=', since newer versions of libs should be compatible, but not here.

So look for a newer version of the package you want to install (maybe it's in backports, too), downgrade your backported lib (or whatever package), or ask the maintainer  of the package you want to install if it is possible to 'extend' the dependency to '>='

---

### Post by c0rderr0y on 2005-08-24
so does this mean I have to install the progs before updating? thats really dumb... what if i want to add something later?!?!

---

### Post by Juergen on 2005-08-25
You probably wouldn't be able to update the lib if there are packages depending on it's version.

The thing to learn here is: it all runs well if you stick to the 'official' Ubuntu repositories.
As soon as you add 3rd-party repositories (even the semi-official backports) prepare for all kinds of problems.

But AFAIK it shouldn't be necessary to have a dependency on the exact version of another packet in most cases.
So you could really ask the maintainer of the troubling package if this is needed, maybe it is just a buglet in the packaging.

---

### Post by c0rderr0y on 2005-08-25
well im using the sources.list from the unofficialubuntu guide.... would that cause me any problems?

---

### Post by Juergen on 2005-08-25
From your first post:> but 3.0.14a-3ubuntu3~5.04ubp1 is to be installedThe ubp in the name shows that this package is from the backports project. 
If you want to read a bit about this project, look here: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

Packages from this project aren't created by their original maintainers, and aren't tested against all 16000 'official' packages. 
If noone complains after a few days they go from 'staging' to 'stable'
You just found a conflict...

BTW: There are extra forums for backports. Maybe you could ask there.

---

### Post by c0rderr0y on 2005-08-25
thanks I am sort of new to this debian stuff i came over from slackware (which is an awsome distro btw) since slackware was difficult to setup on my lappy i wanted something ready to go....

---

