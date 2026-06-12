---
title: "Installing a linksys wireless card"
date: 2005-04-19
forum: Desktop Environments
---

### Post by UbuntuNewb on 2005-04-19
Hi, I installed Kubuntu without a hitch today after putting together my computer.  When I run the 'recompile module method' instructions on [linksys page](http://www.linksys.com/support/support.asp?spid=25#otherdist) i get so many errors by typing the first command I can't even copy them all to the screen.  I'm assuming I'm doing something wrong.  Do I have to recompile the kernel to get this functionality?

thanks for your help!

---

### Post by heimo on 2005-04-19
I'm just guessing here, but you probably don't have gcc (compiler) installed. 
 ```
sudo apt-get install build-essential
``` 

Be sure to search the forum and check comments about your card on this wiki:
[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by UbuntuNewb on 2005-04-20
Looks like my card works if I can compile the ndiswrapper package.

I'm not sure what your protocol is for linking outside this site, so I won't link to it, but the project page for ndiswrapper on sourceforge has a listing of all the cards that work.

Thanks for your help!  Hope I can get this done when I get home.

Edit: and I had gcc installed so it must be some other problem

---

