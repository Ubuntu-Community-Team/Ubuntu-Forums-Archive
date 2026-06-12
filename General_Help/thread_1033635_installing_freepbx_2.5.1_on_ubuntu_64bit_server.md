---
title: "installing freepbx 2.5.1 on ubuntu 64bit server"
date: 2009-01-07
forum: General Help
---

### Post by hosdes on 2009-01-07
I am using a ubuntu 8.04 LTS 64bit server.  I have apt-get install asterisk and all the dependable packages as per instructions, [http://www.freepbx.org/support/documentation/installation/install-process-for-ubuntu-6-06](http://www.freepbx.org/support/documentation/installation/install-process-for-ubuntu-6-06).  When untar freepbx-.2.5.1 and, database and tables set up.

when I go to freepbx directory and type "./install_amp" I get error "-bash: ./install_amp: /usr/bin/php: bad interpreter: No such file or directory".

did some research and found that I should not install asterisk from repos, [http://colt45.chemlab.org/?p=55](http://colt45.chemlab.org/?p=55).

Does anyone know how to solve this?

---

### Post by phisher1 on 2009-01-07
```
sudo apt-get install php5-cli
```

Give that a shot.

---

### Post by hosdes on 2009-01-07
I found the problem.  it was php5-cli not installed.  once I did this and double check all the other depended package I was able to ./install_amp

---

