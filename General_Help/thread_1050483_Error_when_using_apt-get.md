---
title: "Error when using apt-get"
date: 2009-01-25
forum: General Help
---

### Post by CarbineReloaded on 2009-01-25
I was having problems getting my brother 5250 printer installed a while ago..... followed the tips from a few threads on this forum, and got it working.


Unfortunately, I now also get this error message (which started happening after a failed attempt to get the printer working) whenever I install software/update now.


```
Processing triggers for menu ...
Errors were encountered while processing:
 cupswrapperhl5250dn
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


How do I fix this?

---

### Post by x22 on 2009-01-26
try 

"dpkg -P cupswrapperhl5250dn"

or 

"apt-get -f install"

---

### Post by CarbineReloaded on 2009-01-26
> **x22 said:**
> try 

"dpkg -P cupswrapperhl5250dn"

or 

"apt-get -f install"

Those didn't do anything to fix it.

---

### Post by utnubuuser on 2009-01-26
How about good ol' > sudo dpkg --configure -a

---

### Post by CarbineReloaded on 2009-01-26
```

Setting up cupswrapperhl5250dn (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperHL5250DN-2.0.1: 64: cannot create /usr/share/cups/model/HL5250DN.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
cp: cannot stat `/usr/share/cups/model/HL5250DN.ppd': No such file or directory
dpkg: error processing cupswrapperhl5250dn (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperhl5250dn
****@****:~$ lpadmin: No such file or directory


```

---

### Post by utnubuuser on 2009-01-26
Possibly remove the cupswrapper, then reinstall it.

sudo apt-get remove --purge cupswrapperhl5250dn

---

