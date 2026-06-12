---
title: "package manager stuck in loop"
date: 2008-12-08
forum: General Help
---

### Post by JohnsShadow on 2008-12-08
about 2-3 days ago i tryed to install a debian program on my ubuntu system
pacpl 4.03 . deb (perl audio converter)
the installation failed (it died, turned black) i clicked exit not thinking about it
a few days later i tryed to install a diffrent .deb file (this one designed for ubuntu) & it was telling me i already had a package manager running
i checked the system processes and no such package manager was running
i ran dpkg --configure -a and it started to finish the instillation of pacpl
bbut its searching for dependencies relating to a debian system (its hunting down a file off a server that may or may not be there)

i ran apt-get purge --pacpl
and i get an error saying that dpkg is still doing somthing

now its stuck in this loop looking for a file that isnt there
i cant stop it 
and im confused

please HeLP!

i promise i wont try to install a debian package ever again!

---

### Post by malathion on 2008-12-08
It would probably be drastic to never attempt to install another debian package as this would prevent you from installing anything in synaptic or running any software updates through the repositories ;)

Have you tried rebooting the machine? That should close any processes that are hung up.

---

### Post by phidia on 2008-12-08
It seems like you should be able to kill dpkg. "sudo kill dpkg" and then run the purge command-a reboot should work in stopping dpkg also though.

---

### Post by JohnsShadow on 2008-12-08
root@jsx-evil-jsx:/home/jsx# kill dpkg
bash: kill: dpkg: arguments must be process or job IDs
root@jsx-evil-jsx:/home/jsx# kill dpkg pacpl
bash: kill: dpkg: arguments must be process or job IDs
bash: kill: pacpl: arguments must be process or job IDs

well that didnt work

ive rebooted several times, i like to turn my machine off when im not useing it

would you like to try again?

note: this is a root terminal

there is a diffrence from a debian .deb file and a ubuntu .deb file and i found that diffrence today

---

### Post by JohnsShadow on 2008-12-11
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.

this is the error i get when i try to do anything apt-get relateing

this is the terminal error i get when i run dpkg
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://cpan.calvin.edu/pub/CPAN/authors/01mailrc.txt.gz](ftp://cpan.calvin.edu/pub/CPAN/authors/01mailrc.txt.gz)

this is the error i get when opening synaptic

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

