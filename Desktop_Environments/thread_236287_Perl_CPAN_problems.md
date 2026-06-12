---
title: "Perl CPAN problems"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Mr. Brownstone on 2006-08-14
I'm trying to install a few Perl packages but to no avail on a fresh installation of Dapper.

First I try getting the CPAN shell:```
sudo perl -MCPAN -e shell
```I then try installing various modules:```
install Bundle::CPAN
install Date::Manip
install MIME::Base64
install File::Copy
install IO::Socket::Multicast
```Every one of them fails with "make returned bad status, install seems impossible"

Some other threads suggested permissions and "make" installation problems and offered the following solutions:```
sudo apt-get install build-essential
```Logging in as root instead of using sudo:```
sudo su -
```Neither of which have helped.

Thanks to anyone who can offer assistance on this. It all works fine on Fedora Core 5 on my work laptop, but I'd like to avoid switching if at all possible. :cool:

---

### Post by Mr. Brownstone on 2006-08-14
It seems like I've answered my own question, so I'll share what I've learned here.

Actually, I never did find a way to solve my original problem - I just learned how to install manually without using the CPAN Shell. Here's the lowdown:

1. Search for your required modules here: [http://search.cpan.org/](http://search.cpan.org/)

2. Download them. ;)

3. Put them somewhere like ~/perl

4. Run **tar zxvf** against all of your downloaded **.tar.gz** files, then **cd** to their respective folders and type:```
perl MakeFile.PL
make
make test
sudo make install
```Works for me. 8)

---

### Post by llamakc on 2006-08-14
Also, Perl modules are packaged in Ubuntu (Debian-based) as 

libname-name-perl

so 

```

ken@dothan:~$ apt-cache search libdate-manip-perl
libdate-manip-perl - a perl library for manipulating dates

```

---

