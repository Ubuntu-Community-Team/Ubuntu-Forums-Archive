---
title: "I can't reinstall vmware"
date: 2006-06-28
forum: Desktop Environments
---

### Post by thewanabee on 2006-06-28
I initially installed vmware player on my machine, and it worked fine, but I quickly realized that I really wanted vmware workstation so I uninstalled the former and now every time I try to install the latter I get the following:
> 
../vmware-distrib# ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the rpm installer (version 3).

Converting the rpm3 installer database format
        to the tar3 installer database format.

error: package VMwarePlayer is not installed
Failure

Execution aborted.



Any suggestions?

---

### Post by taurus on 2006-06-28
How did you uninstall it and did you remember to remove ~/.vmware as well?

---

### Post by thewanabee on 2006-06-28
I dont recall exactly what I did (it was 3AM and I was in withdrawl from a caffeine high) but I believe that I downloaded the original file as an .rpm and converted it to a .deb using alien. When I went to pull it out, I just did it through adept package manager. As far as your suggestion is concerned: I havent tried that, but it sounds like just as good an ideal as any right about now. I'll try it later when I get home.

---

### Post by thewanabee on 2006-06-29
That suggstion you made didnt pan out, Tarus. However, I did some tinkering and work my way around the problem myself. Basically, I downloaded vmware workstation as an rpm, changed it to a deb using alien with the '--scripts' parameter, installed it in a terminal using 'sudo dpkg -i <name of file>.deb and finally, I ran vmware-config.pl and i was good to go. 

I dont know if thats the most elegant or cleanest method that could have been found, but you know what they say: "Any port in a storm" right?

Thanks for the input though.

---

### Post by Dubbayoo on 2006-06-29
Try removing the pkg with the --purge switch; that should get rid of everything; then remove any vmware dirs in your home directory (unless you have d/led some virtual machines)

---

