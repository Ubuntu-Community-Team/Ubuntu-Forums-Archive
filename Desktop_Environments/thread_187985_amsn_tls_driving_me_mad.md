---
title: "amsn tls driving me mad"
date: 2006-06-03
forum: Desktop Environments
---

### Post by antonika on 2006-06-03
hello

im new to ubuntu, i am trying to install amsn and i have tryed installing it from source, from cvs, from their .deb package and from [http://packages.ubuntulinux.org/dapper/x11/amsn](http://packages.ubuntulinux.org/dapper/x11/amsn) there, they all complain of missing TLS library. which i have also installed atleast a thousand times now ](*,)  :evil: also from tls.sf.net and from the packages.ubuntulinux page tcltls, i have also tryed setting the path to teh tls library in Preferences then advanced in amsn, still no go.. is it supposed to be like this? 

mad

---

### Post by aysiu on 2006-06-03
Can you post the output of this terminal command? ```
sudo aptitude update && sudo aptitude install amsn
```

---

### Post by antonika on 2006-06-04
this

anto@jasika:~$ sudo aptitude update && sudo aptitude install amsn
Password:
Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
Initierar paketstatus... Färdig
Bygger taggdatabas... Färdig
Läs:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper Release.gpg [189B]
Läs:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Läs:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper Release
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates Release
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper/main Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper/restricted Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper/main Sources
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper/restricted Sources
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/main Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/restricted Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/main Sources
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/restricted Sources
Bra [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hämtade 3B på 7s (0B/s)
Läser paketlistor... Färdig
Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
Initierar paketstatus... Färdig
Bygger taggdatabas... Färdig
Inga paket kommer att installeras, uppgraderas eller tas bort.
0 paket uppgraderade, 0 nya installerades. 0 att tas bort och 0 inte uppgraderade.
Behöver hämta 0B arkiv. Efter uppackning kommer 0B att användas.
Skriver utökad statusinformation... Färdig

it says everything is Done and ok

but then I run amsn again, and again it wants to install TLS...

I tryed to trick it into installing it for itself, I went to tls.sf.net and downloaded the 1.4. version from there, which amsn requests, then I put it in /var/www/ which is apache2's root, so that it is acccesible from [http://localhost/here.tar.gz](http://localhost/here.tar.gz) then I changed in autoupdate.tcl in /usr/share/amsn and removed the osdn link and put localhost instead, so that it worked for amsn to "download" the tls package and install it, it said it installed it all correctly and it should work from then now, but lo and behold still it doesnt work.

really weird beause when i had gentoo it worked just fine with the same ~/.amsn but the thing is i tryed moving ~/.amsn to ~/backed/ so that it would have to create a new one.. but still nothing.. 

maybe i should go back to gentoo, where things works hehe ;)

---

### Post by panurge77 on 2006-06-04
try this:


sudo gedit /usr/lib/tls1.50/pkgIndex.tcl


and then change this:
"package ifneeded tls 1.5"
to this
"package ifneeded tls 1.50"

Yes... just add the 0 (zero)

---

### Post by antonika on 2006-06-05
would be nice if i could try that now but i already installed gentoo again, just gotta emerge kde now hehe :)

amsn works fine here and it has tls1.4.1 in pkgIndex it says ifneeded tls 1.4 only.. :roll:

---

### Post by Truthiswithin on 2007-05-19
@Panurge77 - worked for me, thanks :)

---

### Post by nanopete on 2007-05-19
Jep, working fine here too, thanks :)

---

### Post by Yanluo on 2007-05-19
> **panurge77 said:**
> try this:


sudo gedit /usr/lib/tls1.50/pkgIndex.tcl


and then change this:
"package ifneeded tls 1.5"
to this
"package ifneeded tls 1.50"

Yes... just add the 0 (zero)

i know you didnt answer a thread that i had started. but...

F*******N hell yea. FINALLY its working... thank you so very much. spent hours and hours tonight trying to get that app to work... again. thank you:D

---

### Post by killerguy on 2007-05-23
thanks the change with the 0 help thanks alot keep up the good work guys :popcorn:

---

### Post by Xephrey on 2007-05-29
snackar du svenska?

---

### Post by ferrgle on 2007-05-29
thanks for that it works a treat - after I remembered to shutdown aMSN!

---

### Post by psavva on 2007-05-29
Adding the 0 at the 1.5 worked for me too.... Seems to be a bug with amsn...

Thanks :p

---

### Post by jclmusic on 2007-05-29
thanks so much! weird bug though...

---

### Post by ninja_in_pajamas on 2007-05-31
YES!!!  I have been fighting with this for a few days now!  I'm glad I ran across this thread.   :lolflag:

---

### Post by loathsome on 2007-06-01
> **panurge77 said:**
> try this:


sudo gedit /usr/lib/tls1.50/pkgIndex.tcl


and then change this:
"package ifneeded tls 1.5"
to this
"package ifneeded tls 1.50"

Yes... just add the 0 (zero)
Thanks a lot! This really helped me as well.

---

