---
title: "Installing Samba on Warty"
date: 2005-01-27
forum: Desktop Environments
---

### Post by UrbanSlayer on 2005-01-27
Ive just installed Ubuntu on my laptop, ive had it on my desktop for a while and didnt have a problem with installing samba, however I just tried to install it using just the main and universe repo's in my sources list, and got this - 

mizuho@shinobu: $ sudo apt-get install samba         
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.7-1ubuntu6) but 3.0.7-1ubuntu6.3 is to be installed
E: Broken packages

Ive tried using multiverse as well, and have browsed round these forums looking for a reason as to why it says the packages are broken, but I am unsure.  Can anyone help?

Thanks

---

### Post by ilari on 2005-01-27
The latter (3.0.7-1ubuntu6.3) seems to be a security update for the package 'samba-common 3.0.7-1ubuntu6'.  There should also be a 3.0.7-1ubuntu6.3 version of the package 'samba', which has the 6.3-version as a dependency. Try to run 'sudo apt-get update' before running 'sudo apt-get install samba', as this might solve the problem.

---

### Post by UrbanSlayer on 2005-01-27
Tried that, no dice, still comes up with the same error.

---

### Post by tameroski on 2005-02-13
same error for me, also same error when runing "apt-get install smbfs" ...

still no solution ?

---

### Post by Haegin on 2005-05-25
Im getting a very similar error - same thing but with newer versions of samba. If i try to remove the samba-common files it tells me its going to remove other stuff that I still want.

---

