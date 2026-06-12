---
title: "help installing tar.gz"
date: 2009-01-06
forum: General Help
---

### Post by proevofanatik on 2009-01-06
i am trying to install an open source payroll software called paymaster. but it is in tar.gz format

here is the link [http://www.treshna.com/paymaster/download/](http://www.treshna.com/paymaster/download/)

i am on ubuntu 8.10 and was wondering if someone could show me how to make it into a deb package. i want to install this in my works pc for my boss to use.

thanks

---

### Post by tuxxy on 2009-01-06
To install the calculator first extract the contents of the tar.gz file to your desktop, now open a terminal and cd into the folder you just extracted so would be like this

```
cd /home/user/Desktop/NewFolder
```Now to configure

```
./configure
```If it is successful then run make,

```
make
```Finally install the software
```

sudo make install

```

---

### Post by Ahadiel on 2009-01-06
> **proevofanatik said:**
> i am trying to install an open source payroll software called paymaster. but it is in tar.gz format

here is the link [http://www.treshna.com/paymaster/download/](http://www.treshna.com/paymaster/download/)

i am on ubuntu 8.10 and was wondering if someone could show me how to make it into a deb package. i want to install this in my works pc for my boss to use.

thanks
You probably have not installed build-essential either.
```
sudo apt-get install build-essential
```

---

### Post by proevofanatik on 2009-01-07
when i type in ./configure it says
 kevinnicola@kevinnicola-desktop:~/Desktop/paymaster$ ./configure
bash: ./configure: No such file or directory

---

### Post by Slim Odds on 2009-01-07
> **proevofanatik said:**
> when i type in ./configure it says
 kevinnicola@kevinnicola-desktop:~/Desktop/paymaster$ ./configure
bash: ./configure: No such file or directory

README file
> Bond uses Scons for compiling software, not make. You need to make certain you 
download and install scons first. For debian this is apt-get install scons.

Also bonddb and bond must also be installed. See paymaster website under 
requirements for details.

If your upgrading from an older version of paymaster please remove the
/usr/local/lib/pkgconfig/bond*.pc files


---

