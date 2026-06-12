---
title: "How to remove a package"
date: 2006-06-19
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2006-06-19
Hi All,


[http://people.ucsc.edu/~skurapat/archives/2005/10/#e2005-10-17T19_51_00.txt](http://people.ucsc.edu/~skurapat/archives/2005/10/#e2005-10-17T19_51_00.txt)

I got a suggestion in the above site to render telugu font properly. He mentioned to remove ttf-freefont. I request you please let me know how to remove a package.

Regards,

Swaroop Kunduru.

---

### Post by Ramses de Norre on 2006-06-19
How did you install it? For apt use sudo aptitude purge package_name, for dpkg use sudo dpkg -r package_name, for apps compiled from source you'll need to track down the files manually and rm them.

---

### Post by jimbob on 2006-06-19
>apt-get remove ttf-freefont

Or you can use Synaptic and check remove.
________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB IDE 80 GB SATA
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by az on 2006-06-19
[QUOTE=SwaroopKunduru]Hi All,


[http://people.ucsc.edu/~skurapat/archives/2005/10/#e2005-10-17T19_51_00.txt](http://people.ucsc.edu/~skurapat/archives/2005/10/#e2005-10-17T19_51_00.txt)

I got a suggestion in the above site to render telugu font properly. He mentioned to remove ttf-freefont. I request you please let me know how to remove a package.

Regards,

Swaroop Kunduru.[/QUOTE]
Open up synaptic package manager and search for that package.  Right-click on it and select remove.  You will be told that some other packages will be removed along with it.  If you are okay with that, hit apply.

---

