---
title: "How to build a simple deb-package?"
date: 2005-07-06
forum: Desktop Environments
---

### Post by nnacht on 2005-07-06
Hello, dear ubutuforum,
can somebody tell me how to solve my following problem?
I have a software in a local folder, and I would like to make a deb-package from the folder, so that if I use apt-get install, I can get the software installed on somewhere else, say /usr/local. That means that all the deb-package to do is just copy the folder the another destination, no dependency check and so on. 
Somebody told me that I should read the main manuell on ther debian server, but it is for me to complex. Can somebody tell me a simple way?

---

### Post by smack on 2005-07-06
There is no simple way to make a deb. It's just inherently complex.

What's the sorftware? Is it something obscure?

---

### Post by az on 2005-07-06
Debian Women have a presentation on how to make a deb package from scratch (without debhelper) on their website.  Also, Benjamin Mako Hill recently gave a presentation on making a simple deb.

Use Google.   However, I think that your issue is best served using a tarball?  If you do not have dependancies, what is the point of a deb?

---

### Post by shakin on 2005-07-06
[QUOTE=azz]I think that your issue is best served using a tarball?  If you do not have dependancies, what is the point of a deb?[/QUOTE]

Can't Alien make a deb from a tarball? I think that would be the easiest solution.

---

### Post by az on 2005-07-07
[QUOTE=shakin]Can't Alien make a deb from a tarball? I think that would be the easiest solution.[/QUOTE]

I think slackware packages (tgz) are more than just tarballs.  I am not sure.

---

### Post by dewey on 2005-07-07
I'm not inherintly familiar with creating deb packages, but if you were to create one, you would not install it with apt-get.  Apt accesses repositories, and unless you had created one yourself, or created an application everyone wanted, thus warranting it's inclusion in the repository, you would simply use
```
$sudo dpkg -i <PackageNameAndLocation>
```
Example:```
$sudo dpkg -i /home/aaron/aaronsnewfile.deb
```

---

### Post by manicka on 2005-07-07
If you're making one from source you can use in the extracted source folder

./configure
make
sudo checkinstall

checkinstall will install the package and make a nice deb package for you. This installed package will also show up in apt/synaptic and can be removed with these tools if needed. 

Use dpkg to install stand alone deb's... sudo dpkg -i packagename.deb

I thought Alien was only for converting RPM's?

---

