---
title: "HOw to upgrade?"
date: 2009-04-25
forum: General Help
---

### Post by tanveerahmed2k8 on 2009-04-25
im on ubuntu 8.10... i downloaded the iso for 9.04 .. i have g iso mount...
i mounted it on cdrom0
and it got mounted but nothing happens..
it doesnt say to upgrade or install or nothing..
what do i do to upgrade ( i have the iso )

---

### Post by kpkeerthi on 2009-04-25
You can find the instructions [here]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")

---

### Post by Monotoko on 2009-04-25
You dont need the ISO, just open up your update manager (System -> Administration -> Update Manager)

and at the top it will tell you that a new distrobution is out

---

### Post by lisati on 2009-04-25
Does a window open asking you if you want to start the package manager? If so, you should be able to select the option to upgrade.

Another method of upgrading is to open System->Administration->Update Manager. If it recognizes that there is a new distribution available (it should with 8.10) you will be able to upgrade from there.

---

### Post by sahabcse on 2009-04-25
Put the cd and open the terminal
sudo apt-cdrom add
sudo apt-get update
sudo apt-get upgrade

---

### Post by tanveerahmed2k8 on 2009-04-26
i downloaded the ISO for no reason...

---

