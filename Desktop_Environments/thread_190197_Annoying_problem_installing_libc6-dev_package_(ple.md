---
title: "Annoying problem installing libc6-dev package (please help)"
date: 2006-06-06
forum: Desktop Environments
---

### Post by eitce on 2006-06-06
Hi,

I am trying to get my c++ compiler working, and it seems to be missing some required libraries.  I think I need to get the build-essential package, but when I do:

'apt-get install build-essential', I get the error:
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                           libc-dev

Then when I try 'apt-get install libc6-dev' I get:
libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu15) but 2.3.5-1ubuntu12.5.10.1 is to be installed

I don't really understand what this means.  It seems to be saying I need a different version of libc6-dev.  When I tried to do a force package version in the synaptic package manager, it threatened to remove like 100 other dependent packages, so I aborted.

My sources.list file looks like (with comments removed):

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

Why can't I get this to work?  I was able to install all this stuff on my Ubuntu laptop a month ago and I don't think i did anything too differently.  Thanks for any help.

---

### Post by bluevoodoo1 on 2006-06-06
What release are you using? Hoary? Breezy? Dapper?

If you're using Breezy or Dapper, this will help with the sources...
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by eitce on 2006-06-07
Thanks man, that worked great.  I am using Breezy and the sources they listed there allowed me to apt-get build-essential.

---

