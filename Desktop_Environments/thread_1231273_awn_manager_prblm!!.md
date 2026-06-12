---
title: "awn manager prblm!!"
date: 2009-08-04
forum: Desktop Environments
---

### Post by harivittal.hk on 2009-08-04
hi everyone..
i'm trying to install awn manager ...m an intrepid user...
this is the problem m facing...the dependencies r not available..how can i install awn..

" python-awn-trunk:
           Depends: libawn0-trunk (= 0.3.3~bzr566-1.8.04) but it is not going to be installed
           Depends: libffi4 but it is not installable"

any support is appreciated.

---

### Post by harivittal.hk on 2009-08-04
hi everyone..
i'm trying to install awn manager ...m an intrepid user...
this is the problem m facing...the dependencies r not available..how can i install awn..

" python-awn-trunk:
Depends: libawn0-trunk (= 0.3.3~bzr566-1.8.04) but it is not going to be installed
Depends: libffi4 but it is not installable"

any support is appreciated.

---

### Post by hetx on 2009-08-04
```
sudo apt-get install avant-window-navigator
```

---

### Post by realzippy on 2009-08-04
Did you add the sources?:

deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) intrepid main

---

### Post by harivittal.hk on 2009-08-04
thanks for the rply..
no  i haven't added that..
can u plz guide me how to do it..

---

### Post by harivittal.hk on 2009-08-04
hi..thanks for rply..
i ran that code on terminal..
it asked for dependicies lik python-trunk,so when i gave tat i got the error that i hav posted..

---

### Post by realzippy on 2009-08-04
Open a terminal.Type:

**sudo gedit /etc/apt/sources.list**

Then,edit at the bottom of the sources list:

[B]deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) intrepid main
[/B]

Save and close the list,go back to terminal,type

**sudo apt-get update**

To install AWN type :

**sudo apt-get install avant-window-navigator**

---

### Post by harivittal.hk on 2009-08-04
:confused:
hi friends,
i am facing a new serious problem now,i was working with AWN manager for sometime and wanted to install a pidgin screenlet,so tried to open synaptic manager..but its not opening..i even restarted the system..the same problem exists...m not able to see the synaptic even on the dock..
plz help..
any support is appreciated..

---

### Post by realzippy on 2009-08-05
Open a terminal,type:

**sudo apt-get clean**
**sudo apt-get update**

and try again..any result?

..can you open synaptic on a terminal?Type:

**sudo synaptic**

---

