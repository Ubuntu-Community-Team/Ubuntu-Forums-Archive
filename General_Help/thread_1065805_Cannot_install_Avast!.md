---
title: "Cannot install Avast!"
date: 2009-02-10
forum: General Help
---

### Post by Justin18 on 2009-02-10
Hello, 

Everytime I try to Install Avast! antivirus for Linux I download the .deb file and I double click it to try to install with the "Install package" option but every-time I double click it I get 
Error: Wrong architecture 'i386' is there any workaround for this?

-Justin

---

### Post by UbuntuNerd on 2009-02-10
is there any particular reason you want to use "avast"

---

### Post by LowSky on 2009-02-10
[http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/](http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/)

and what UbuntuNerd was getting at is you dont really need antivirus on a Linux Computer, as no Viruses or malware exist for Linux computers, because of the very few people using it and due to the security protocols that Linux impliments

---

### Post by Justin18 on 2009-02-10
Hello, 

Thank you for your quick replies. 
Yes I know there are No Viruses (Malware) for Linux the reason why I wish to have a AV solution for on Ubuntu is to scan and try to prevent the spread of Malware files (even if they are un-operable) under Ubuntu the reason is because I am duel booting Ubunty 8.10 and Windows XP and I I guess you could say Battle Malware on Windows its a hobby as well as my job. But thanks the replies are appriciated

---

### Post by overlord.gaurav on 2009-02-10
Try this in a terminal:
```
dpkg -i --force-architecture avast4workstation_1.3.0-2_i386.deb
```

---

### Post by jespdj on 2009-02-10
This happens because you are running the 64-bit version of Ubuntu and you're trying to install a package made for 32-bit Ubuntu on it.

Note that 32-bit software does run on 64-bit Ubuntu, but you have to do some extra work to install it. You can force-install a 32-bit package like this:
```
sudo dpkg -i --force-architecture filename.deb
```
But you might need to install the necessary 32-bit libraries manually if you do this (32-bit software needs 32-bit libraries; it can't use the 64-bit libraries that are on your system). There's a script called getlibs that can automatically find out what 32-bit libraries a certain program needs and install them for you.

I agree with the above posters that it's a waste of time and system resources to run antivirus software on Ubuntu. Ubuntu is not Windows - it's fundamentally more safe so that you will not get a virus on Ubuntu, and you don't need antivirus software.

---

### Post by YMS_1975 on 2009-04-17
This thread just saved me the hassle of having to ask you all for directions on installing Avast on my 64-bit Ubuntu (laptop).

Just felt like sharing. :D

The more I use Ubuntu, the more I grow fond of it's perks (stable, no viruses/malware, ummmm...IT'S FREE!).

Later.

---

