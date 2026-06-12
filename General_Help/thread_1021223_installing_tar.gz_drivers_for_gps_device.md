---
title: "installing tar.gz drivers for gps device"
date: 2008-12-25
forum: General Help
---

### Post by vivek_yadav on 2008-12-25
i'm trying to make my gps device work with linux. i found a program [bt747]("http://bt747.wiki.sourceforge.net/") to connect to the device. but the USB drivers i found from the gps device's website are in form of tar.gz
how do i install them?

here's the link to the tar.gz drivers file [https://www.silabs.com/Support%20Documents/Software/cp210x-3.0.0.tar.gz](https://www.silabs.com/Support%20Documents/Software/cp210x-3.0.0.tar.gz)

these are the files in the archive
<folder>rpm
>>brp-java-repack-jars
>>brp-python-bytecompile
>>check-rpaths
>>check-rpaths-worker

<folder>cp210x
>>configure
>>cp210x.h
>>installmod
>>Makefile26
>>cp210x.c
>>defaults.mk
>>Makefile24
>>Rules.make

copying
cp210x-3.0.0.spec
makerpm
readme
REPORTING-BUGS
install
PACKAGE-LIST
RELEASE-NOTES

---

### Post by Nepherte on 2008-12-25
Did you read the readme or install file? In those files you often find additional information about how to install it. It generally goes as follows:
```
./configure
make
sudo make install

```
If any of these produce an error there's no point in going on to the next command. It mostly fails compiling because it depends on some kind of library or other program (a so-called dependency problem).

But before you can compile anything, you need some extra packages:
```
sudo apt-get install build-essential linux-headers-`uname-r`
```

---

### Post by balaknair on 2008-12-25
This is a source tarball.
Installing this particular package creates an RPM package but Ubuntu uses the .deb package system. So you will have to use the 'alien' package to convert and install it as deb.

Open a terminal- Applications menu> Accessories> Terminal and type or copy paste the following commands to
1) Install Alien:
```
sudo apt-get install alien
```

2) Copy the tar.gz into the Desktop, and in the Terminal enter(one line at a time, this may take a while)
```
cd Desktop

gzip -cd cp210x-3.0.0.tar.gz | tar xvf -

cd cp210x-3.0.0

./makerpm

cd /var/tmp/silabs/rpmbuild/RPMS/i386

sudo alien --to-deb -scripts cp210x-3.0.0-001.i386.rpm

sudo dpkg -i ./cp210x_3.0.0-2_i386.deb
```



NOTE: when entering your password in the terminal, you will not see any *** symbols appearing as you type, just type the password carefully and press 'Enter"

---

### Post by vivek_yadav on 2008-12-25
got it installed. with small command changes coz my arch is 64bit.. thanks a lot. hope the program works now.

---

### Post by balaknair on 2008-12-25
Glad to help
All the best, and Happy Holidays :D

---

### Post by weatherfront on 2008-12-26
I am trying to install the latest CP210X 3.0.0 driver into 2.6 kernel. Toward the end of ./makerpm I am getting>>>>>

make: *** /lib/modules/2.6.23.9-linutop-7/build: No such file or directory.  Stop.
make: *** [modules] Error 2
error: Bad exit status from /var/tmp/rpm-tmp.34575 (%build)


RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.34575 (%build)

<<<<<and the make fails.

Please can someone point me at what is missing?

---

### Post by vivek_yadav on 2008-12-27
i followed the make rpm instructions and didnt receive errors. i'm new to linux and not sure what the commands meant but they worked fine for me.
after the rpm was created, i used alien to make it into debian package and installed by just double clicking in file browser. and after that my gps was working with bt747.

---

### Post by balaknair on 2008-12-27
@Weatherfront: 

> make: *** /lib/modules/2.6.23.9-**linutop**-7/build: No such file or directory. Stop.
make: *** [modules] Error 2
error: Bad exit status from /var/tmp/rpm-tmp.34575 (%build)


RPM build errors:
Bad exit status from /var/tmp/rpm-tmp.34575 (%build)

<<<<<and the make fails.

Are you using a Linutop miniPC?
Linutops use a highly customised compressed version of Ubuntu 8.04, modified to fit into a 1 GB flash disk. I don't think the steps outlined here would work on a Linutop machine. There may be workarounds available, but I'm afraid I have absolutely no idea about what they are or where to find them. My advice would be to contact the manufacturer for advice. Don't try to force an install, it might be in violation of your warranty terms.

---

