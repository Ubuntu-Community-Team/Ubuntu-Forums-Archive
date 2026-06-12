---
title: "gam_server issue"
date: 2006-03-04
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-03-04
Whenever I load a lot of files into my playlist in amarok a process called gam_server shows up and starts to take a lot of my cpu. It doesn't go away untill I stop it myself and keeps on eating more cpu..
I've searched the forums but didn't find any useful info..

[http://www.ubuntuforums.org/showthread.php?t=74908&highlight=breezy+gam_server]("http://www.ubuntuforums.org/showthread.php?t=74908&highlight=breezy+gam_server")
The method there does stop the process permanentaly but I always need to reload my folders then. (gets annoying after a while).
Does anyone know how to fix it without the need to disable the service?

---

### Post by Ramses de Norre on 2006-03-05
Anyone who knows a solution to this?

---

### Post by PunkDuck on 2006-03-08
I got the newest packages from the debian site... 

had to upgrade following packages and everything works fine for me now:
gamin_0.1.7-3_i386.deb
libgamin0_0.1.7-3_i386.deb
libglib2.0-0_2.8.6-1_i386.deb

This is small how to:

wget [http://ftp.de.debian.org/debian/pool/main/g/glib2.0/libglib2.0-0_2.8.6-1_i386.deb](http://ftp.de.debian.org/debian/pool/main/g/glib2.0/libglib2.0-0_2.8.6-1_i386.deb)
wget [http://ftp.de.debian.org/debian/pool/main/g/gamin/gamin_0.1.7-3_i386.deb](http://ftp.de.debian.org/debian/pool/main/g/gamin/gamin_0.1.7-3_i386.deb)
wget [http://ftp.de.debian.org/debian/pool/main/g/gamin/libgamin0_0.1.7-3_i386.deb](http://ftp.de.debian.org/debian/pool/main/g/gamin/libgamin0_0.1.7-3_i386.deb)
dpkg -i libglib2.0-0_2.8.6-1_i386.deb
dpkg -i *gamin*_0.1.7-3_i386.deb

Greetz,
Stefaan

---

