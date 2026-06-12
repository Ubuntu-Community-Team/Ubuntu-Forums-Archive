---
title: "Need some help with Cinelerra"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Saist on 2006-08-15
Alright, I'm trying to install Cinelerra, using the instructions located here for ubuntu : [http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

This is what my current sources list looks like:

[INDENT]# Ubuntu foundation packages
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted 
# Security updates
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted 
# Package updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
# Backports of newer packages--unsupported and not thoroughly tested
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted 


# Free unsupported packages from Debian and beyond
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe 
# Non-free unsupported packages from Debian and beyond
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse 
# Backports of newer packages--unsupported and not thoroughly tested
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports universe multiverse 


# Cpiherfunk--some packages not available elsewhere
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main 

deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./ 
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/) ./ [/INDENT]


I'm using Synaptic, and the following is a list of errors I get when I try to install Cinelerra

[INDENT]cinelerra:
 Depends: libquicktimehv but it is not going to be installed
 Depends: libquicktimehv but it is not going to be installed[/INDENT]

Okay. Force libquicktimehv

[INDENT]libquicktimehv:
  Depends: libfaac0 (>=1.24+cvs20060416) but 1.24clean-0ubuntu4 is to be installed
  Depends: libfaad2-0 (>=2.0.0+cvs20060416) but 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 is to be installed[/INDENT]


Alright, do a search for 1.24clean-0ubuntu4 : not found. Do a search for libfaac0

Libfaac0 is installed and the readme is located in: /usr/share/doc/libfaac0

This information is provided
[INDENT]
faac (1.24clean-0ubuntu4) dapper; urgency=low

  * The -dev package has to Depend on libmp4v2-dev

 -- Sebastian DrÃ¶ge <slomo@ubuntu.com>  Tue,  6 Dec 2005 20:37:24 +0100[/INDENT]


Libfaad2-0 is also installed, to the most recent version. This information is provided there:

[INDENT]faad2 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) dapper; urgency=low

  * 01_systems.h.diff:
    + Fix the config.h include to mp4_config.h and copy config.h to
      /usr/include/mp4_config.h. Bad bad upstream

 -- Sebastian DrÃ¶ge <slomo@ubuntu.com>  Wed,  9 Nov 2005 18:42:24 +0100[/INDENT]


Basically, I can't tell what the problem is. The installation appears to be complaining about needing files that are already installed...

What should I do from here to fix this?

---

