---
title: "SOGO install"
date: 2010-06-18
forum: Desktop Environments
---

### Post by geo3d on 2010-06-18
I'm looking for any of you experts who have had success in getting SOGO installed. 

I'm using Ubuntu 8.0.4.4 LTS

A quick overview of what I've tried with no success:

1) An apt-get of sogo results in > The following packages have unmet dependencies:
  sogo: Depends: gnustep-base-runtime (>= 1.16.1) but 1.14.1-2ubuntu1 is to be installed
        Depends: libgnustep-base1.16 (>= 1.16.1) but it is not installable
        Depends: libsope-appserver4.9 (>= 4.9.r1664.20100618) but it is not going to be installed
        Depends: libsope-core4.9 (>= 4.9.r1664.20100618) but it is not going to be installed
        Depends: libsope-gdl1-4.9 (>= 4.9.r1664.20100618) but it is not going to be installed
        Depends: libsope-ldap4.9 (>= 4.9.r1664.20100618) but it is not going to be installed
        Depends: libsope-mime4.9 (>= 4.9.r1664.20100618) but it is not going to be installed
        Depends: sope4.9-libxmlsaxdriver but it is not going to be installed
        Depends: sope4.9-db-connector
E: Broken packages2) Using this tutorial [HTML]http://wiki.mhcsoftware.de/SOGo_1.0.1_on_Ubuntu_9.04[/HTML](and I do realize it's for 9.0 - an 
> apt-get install libgnustep-base1.16-libffi results in not found.
3)Using this method [HTML]http://www.linuxjournal.com/magazine/scalable-opengroupwareorg?page=0,0[/HTML]on page 2 > Do
echo $GNUSTEP_LOCAL_ROOT, and remember the value, as it will be required
shortly. the echo results in no value given. 

This last attempt is the furthest I've gotten in attempting to get SOGO installed.
I'd appreciate any other reference or insight anyone might be willing to share.

I apologize in advance if my post is unclear of missing any information you may need.

---

### Post by ronnielsen1 on 2010-06-18
Try one of the deb packages from here.

[http://www.sogo.nu/downloads/backend.html](http://www.sogo.nu/downloads/backend.html)

I don't see one for 8.04 and you might have library issues. Is there any reason you haven't updated a little?
> **Nightly Ubuntu Packages for Intrepid/8.10 and Karmic/9.10**



---

### Post by geo3d on 2010-06-18
I'll that package;

Regarding updates: this box is a new install given to me to get SOGO going.

Thanks for the reply though. Going to check on that package now.

---

### Post by Bucky Ball on 2010-06-18
8.04 is an LTS release. It is still current.

---

### Post by geo3d on 2010-06-18
Update to 8.10 has allowed me to install sogo properly. thank you for the help.

---

### Post by ronnielsen1 on 2010-06-19
> Update to 8.10 has allowed me to install sogo properly. thank you for  the help.
Glad it worked!
>  		8.04 is an LTS release. It is still current. 	
Then you run across a new package you want to install and you either have to get an older version of the package using older lib files or you run across issues like Error: Dependency not satisfiable:  needs foo 1.456 but foo 1.431 is  installed instead

---

