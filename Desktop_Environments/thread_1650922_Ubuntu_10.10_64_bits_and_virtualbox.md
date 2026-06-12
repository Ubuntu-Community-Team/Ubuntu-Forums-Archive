---
title: "Ubuntu 10.10 64 bits and virtualbox"
date: 2010-12-22
forum: Desktop Environments
---

### Post by fernandoch on 2010-12-22
Hello,

I have an ubuntu 10.10 64 bits.

I am getting this error while trying to install virtualbox

```
fernando@localhost:~$ sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'virtualbox-3.2' instead of 'virtualbox'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 virtualbox-3.2 : Depends: libqt4-network (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqt4-opengl (>= 4:4.5.3) but it is not going to be installed
E: Broken packages
```

Very weird. Then I try to install the dependencies and I get that

```
fernando@localhost:~$ sudo apt-get install libqt4-network
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-network : Depends: libqt4-dbus (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
                  Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
E: Broken packages
```

Any clues about what could be wrong? Never had these problems before...

---

### Post by Kirboosy on 2010-12-22
Try downloading the 64 Bit version manually and install it that way. Let me know if this doesn't work for you...

[http://download.virtualbox.org/virtualbox/4.0.0/virtualbox-4.0_4.0.0-69151~Ubuntu~maverick_amd64.deb](http://download.virtualbox.org/virtualbox/4.0.0/virtualbox-4.0_4.0.0-69151~Ubuntu~maverick_amd64.deb)

---

### Post by sikander3786 on 2010-12-22
Try,

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install -f virtualbox
```

If there are still some errors, please post the output of the above mentioned as well these commands.

```
cat /etc/apt/sources.list
```

```
ls -l /etc/apt/sources.list.d
```

---

### Post by fernandoch on 2010-12-22
Thank you guys, but what I did was to remove all libqt4* packages and did the apt-get install virtualbox again and it worked like a charm.

As I said before, never had this problem before...

Thank you all again!

---

### Post by Kirboosy on 2010-12-22
Go ahead and mark this thread as solved then. (Under Thread Tools)

Glad I could help

---

