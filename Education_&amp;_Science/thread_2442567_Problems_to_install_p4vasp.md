---
title: "Problems to install p4vasp"
date: 2020-05-04
forum: Education &amp; Science
---

### Post by rodrigo-mantovani on 2020-05-04
Hello!
I am trying to install p4vasp in Ubuntu, but there is some errors during the installation.

Trial 1: sudo apt install p4vasp (or sudo apt-get install p4vasp or usudo apt-get install -y p4vasp)
Error: Impossible to find package p4vasp

Trial 2: Follow the steps in [https://github.com/orest-d/p4vasp](https://github.com/orest-d/p4vasp)
2.1 Install dependencies via sudo apt-get install python-dev g++ libx11-dev mesa-common-dev libglu1-mesa-dev python-opengl python-numpy python-glade2
Error: Impossible to find package python-glade2

2.2 Install dependencies via sudo apt-get install python-epydoc doxygen
Error: Impossible to find package python-epydoc

2.3 Command make local (or make install)
Error: /bin/sh: 1: python: not found

Can anyone help me? I am quite new to Linux....
Thank You!

---

### Post by p4vaspwien on 2021-04-08
sudo apt-get install python

cd ~/Downloads
wget -c [http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-gtk2_2.24.0-5.1ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-gtk2_2.24.0-5.1ubuntu2_amd64.deb)
sudo apt-get install ./python-gtk2_2.24.0-5.1ubuntu2_amd64.deb

wget -c [http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-glade2_2.24.0-5.1ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-glade2_2.24.0-5.1ubuntu2_amd64.deb)
sudo apt-get install ./python-glade2_2.24.0-5.1ubuntu2_amd64.deb

#download and extract the p4vasp folder, in the home for exaple, then:cd

cd ~/p4vasp-0.3.30
install/install-ubuntu-dependencies.sh
sudo apt update
sudo apt upgrade
make local
#you may need to install some libraries and dipendecies, just look on google how to do it
make install
sudo ./p4v

---

### Post by erynsisk on 2021-04-15
> **p4vaspwien said:**
> sudo apt-get install python

cd ~/Downloads
wget -c [http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-gtk2_2.24.0-5.1ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-gtk2_2.24.0-5.1ubuntu2_amd64.deb) [SIZE=1][[COLOR=#ffffff]five nights at freddy's[/COLOR]]("https://fivenightsatteddys.com")[/SIZE]
sudo apt-get install ./python-gtk2_2.24.0-5.1ubuntu2_amd64.deb

wget -c [http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-glade2_2.24.0-5.1ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-glade2_2.24.0-5.1ubuntu2_amd64.deb)
sudo apt-get install ./python-glade2_2.24.0-5.1ubuntu2_amd64.deb

#download and extract the p4vasp folder, in the home for exaple, then:cd

cd ~/p4vasp-0.3.30
install/install-ubuntu-dependencies.sh
sudo apt update
sudo apt upgrade
make local
#you may need to install some libraries and dipendecies, just look on google how to do it
make install
sudo ./p4v
Thanks for this thoughtful response. This helps quite a bit. Cheers!

---

