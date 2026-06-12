---
title: "Alien"
date: 2005-10-26
forum: Desktop Environments
---

### Post by rj686 on 2005-10-26
I installed alien in order to convert rpm's to debian packages. BUt i heard i need to install RPM in order to use it? WHere can i find that? I cant seem to find just what i need from [http://www.rpm.com](http://www.rpm.com)

---

### Post by dbott67 on 2005-10-26
I don't think you need RPM in order to convert .rpm to .deb, only for converting .deb to .rpm.  

*EDIT: actually, I just checked Synaptic for the dependencies and it does download RPM as one of the dependencies, as well as a few others.*

So, if you use Synaptic or apt-get, it will get everything you need.

-Dave

---

### Post by Xian on 2005-10-26
If you're having difficulty performing a conversion, just post a link to the RPM file you are working with (if available), and post the output of your alien command session.

---

### Post by rj686 on 2005-10-26
sh: -c: line 0: `LANG=C rpm -qp --queryformat %{SUMMARY} point2play-2.0.2-1.i386.(osloskop.net).rpm'
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} point2play-2.0.2-1.i386.(osloskop.net).rpm":  at /usr/local/share/perl/5.8.7/Alien/Package.pm line 466.

thx guys.....

this is what i typed into terminal:
sudo alien --to-deb point2play-2.0.2-1.i386.\(osloskop.net\).rpm

---

### Post by dbott67 on 2005-10-26
Try this command:
```
sudo alien -i point2play**<tab>**.rpm
```

(at the **<tab>** just press your TAB key to auto-complete the filename).

-Dave

---

### Post by rj686 on 2005-10-26
same error :(


rj@LOFTNESS:~/Incoming$ sudo alien -i point2play-2.0.2-1.i386.\(osloskop.net\).rpm
sh: -c: line 0: syntax error near unexpected token `('
sh: -c: line 0: `LANG=C rpm -qp --queryformat %{SUMMARY} point2play-2.0.2-1.i386.(osloskop.net).rpm'
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} point2play-2.0.2-1.i386.(osloskop.net).rpm":  at /usr/local/share/perl/5.8.7/Alien/Package.pm line 466.rj@LOFTNESS:~/Incoming$

---

### Post by rj686 on 2005-10-26
bump

---

### Post by rj686 on 2005-10-26
"to convert packages to or from rpms, you need the Red Hat Package Manager"
[http://www.kitenet.net/programs/alien/](http://www.kitenet.net/programs/alien/)
it said that right on alien's main website. I dont know which rpm package to instal  or where to get itl????

---

### Post by dbott67 on 2005-10-26
Did you install alien using apt-get or Synaptic?  If so, the dependencies would have been installed.

Open Synaptic and re-install alien to be sure.  If you look at the properties of alien, it will list the dependencies.

-Dave

---

### Post by rj686 on 2005-10-26
nope i installed the source version i found somwhere else. Thx for the help man :)

---

### Post by dbott67 on 2005-10-26
No problem!  :)

Let us know if you get it working.

-Dave

---

### Post by rj686 on 2005-10-26
how do i uninstall my old alien binary cuz i think when i type "alien" in terminal its still refering to my old version?
cuz im still getting the old error but i know synaptic installed "lib4rpm" and "rpm"

---

### Post by dbott67 on 2005-10-26
Did you compile it yourself?

If you did, you can use:
```
make uninstall
```
(if you kept the sources). 

If not, you can download the source again and:
```
./configure
make uninstall
```

---

### Post by rj686 on 2005-10-26
it says uninstall is not safe and

j@LOFTNESS:~/Desktop/Incoming/alien$ sudo make uninstall

Uninstall is unsafe and deprecated, the uninstallation was not performed.
We will show what would have been done.

no packlist file found:  at /usr/share/perl/5.8/ExtUtils/Install.pm line 318.
make: *** [uninstall_from_sitedirs] Error 2

---

### Post by rj686 on 2005-10-27
bump

---

