---
title: "i want to force in old kate"
date: 2007-02-02
forum: Desktop Environments
---

### Post by mysticmike on 2007-02-02
i'm currently using the xubuntu edgy live cd on my laptop. the laptop has limited harddrive
and xubuntu seems perfect for it however there is one kde app that i'm still relient on
kate

when i install kate from the synaptic i get a "broken" version with no project file support
and some feature called sessions that i do not want or need. this is the new version of 
kate and it is crap, so i need to install the old version from breazy.

i have downloaded the kate package from breazy and it install fine using 

dpkg -i --force-all 

or

dpkg -i --force-downgrade

the old kate seems to work fine but synaptic says the package is broken and insists on
reinstalling the newer broken kate

is there a correct way to force in this package and not stop apt from fuctioning ????

is there another way to solve this problem like a package of old kate compiled
for edgy or the plugin for new kate to read project files as a deb package.??????

note: i want to solve this without compiling anything. the laptop has a small harddrive
and i do not want to have to install a whole load of kde dev packages (they won't install to 
ramdisk using live cd i have tried to build the plugin this way)  

have the same problem with dapper on my desktop pc

help us out please!

---

### Post by mysticmike on 2007-02-04
sorted it

i hacked control file in the deb package

thats forced it in allright

---

