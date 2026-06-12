---
title: "Uninstall Kubuntu"
date: 2011-03-21
forum: Desktop Environments
---

### Post by superstarks on 2011-03-21
I decided to give Kubuntu a try and since I did I had some problems with my sound card (nothing major, but I want to go back to the pure Gnome Ubuntu). I tried the command located at this link [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) but ended up getting up an error in my terminal that read:

Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
E: Broken packages


This isn't the end of the world if I can't understand the KDE and go back to pure Gnome.. but if anyone has any suggestions it would be greatly appreciated.

I'm running Ubuntu 10.10 and I tried the KDE uninstall from Gnome desktop.

Thanks!

---

### Post by zvacet on 2011-03-22
```
sudo apt-get -f install
```

Witch version of Ubuntu do you run?

---

