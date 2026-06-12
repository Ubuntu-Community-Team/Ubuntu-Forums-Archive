---
title: "Installing Postal Fudge Pack in 9.04 64-bit?"
date: 2009-09-10
forum: Gaming &amp; Leisure
---

### Post by R3mix on 2009-09-10
I just switched from Debian Lenny to Ubuntu 9.04 earlier today.  When I try to run the installer for Fudge Pack, I get the following:

```
r3mix@rockcrawler:/media/cdrom0$ sudo sh linux_installer.sh 
Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing The Postal Fudge Pack for x86 GNU/Linux.................................................................
./setup.sh: 267: /home/r3mix/.setup6498: not found
./setup.sh: 282: /home/r3mix/.setup6498: not found
The setup program seems to have failed on amd64

Fatal error, no tech support email configured in this setup
```

I've been googling around, and can't seem to find any solutions.  Any help is appreciated.

---

### Post by Perfect Storm on 2009-09-11
First, you did install ia32-libs first? If not try that first and try again, next;


```
sudo apt-get install ia32-libs
cd /media/cdrom0
linux32 ./linux_installer.sh
```

or

```
sudo apt-get install ia32-libs
cp -r /media/cdrom0/linux_installer.sh ~/Desktop
cd ~/Desktop
chmod +x linux_installer.sh
linux32 sh linux_installer.sh
```

---

### Post by Kwijt on 2011-03-29
I get this:

Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing The Postal Fudge Pack for x86 GNU/Linux.................................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
./setup.sh: line 148: 23579 Segmentation fault      "$setup" "$@"


I hope somebody has a solution

---

### Post by saturnoyo on 2011-04-12
Hi, I use Ubuntu 10.10 and I have the same problems.

I have read that with a virtual machine with OpenSuse it can work...

¿what can I do?

Thanks.

PS: I am sorry, my English isn't very good... I'm spanish.

---

