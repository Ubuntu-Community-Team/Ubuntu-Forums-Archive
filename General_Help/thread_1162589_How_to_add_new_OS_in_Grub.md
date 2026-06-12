---
title: "How to add new OS in Grub"
date: 2009-05-17
forum: General Help
---

### Post by Baron86Gr on 2009-05-17
I found my ex hard drive with windows XP and tried to add it to the grub editor of Kubuntu so that sometimes i could boot to Windows! how ever i dont know if adding a new one is just enough and i dont know what Root and chain loader to use.. It says its in /dev/sdb so how do i know which (hd*,*) to use in root ( Its not in suggestions ) and what chainloader to use.. It sasys the default is +1. moreover do i have to do anything more?? :( when i used chainloader +1 and root hd(1,0) i had a starting up aften i choose in the boot and nothing else.... Some help please?

---

### Post by zvacet on 2009-05-18
```
sudo fdisk -l
```

With this command you will see where is your OS ( whitch partition on sdb)

Read [this]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands") and I think you will find your way.

---

