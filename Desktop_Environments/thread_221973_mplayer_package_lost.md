---
title: "mplayer package lost?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-24
I have made a Ubuntu's fresh installation, but I can't find the mplayer package.

I have made several times aptitude update

aptitude install mplayer, doesn't find the package

aptitude search cache mplayer, return this:

> p   aolserver4-nscache              - AOLserver 4 module: Tcl API for AOLserver
p   apt-cacher                      - caching system for Debian package and sour
p   ccache                          - Compiler results cacher, for fast recompil
p   cl-rsm-cache                    - Common Lisp Cache Library
p   compilercache                   - a caching wrapper around compilers to spee
v   global-assembly-cache-tool      -
p   kcachegrind                     - visualisation tool for valgrind profiling
p   kcachegrind-converters          - format converters for KCachegrind profilin
p   kmplayer                        - media player for KDE
p   kmplayer-base                   - Base files for KMPlayer
p   kmplayer-doc                    - Handbook for KMPlayer
p   kmplayer-konq-plugins           - KMPlayer plugin for KHTML/Konqueror
p   libcache-cache-perl             - Managed caches of persistent information
p   libcache-fastmmap-perl          - Mmmap'ed file as a shared memory interproc
p   libcache-memcached-perl         - Cache::Memcached - client library for memc
p   libcache-mmap-perl              - Shared data cache using memory mapped file
p   libcache-perl                   - the Cache interface
p   libcache-simple-timedexpiry-per - Perl module to cache and expire key/value
p   libfile-cache-perl              - File::Cache, a filesystem-based object sto
p   libhttp-cache-transparent-perl  - Perl module used to transparently cache HT
p   libipc-sharedcache-perl         - perl IPC::SharedCache - manage a cache in
p   liboscache-java                 - High performance and widely used J2EE cach
p   libroxen-programcache           - Program cache utility module for the Roxen
p   libtie-cache-perl               - perl Tie::Cache - LRU Cache in Memory.
p   libxfontcache-dev               - X11 font rasterisation library (developmen
p   libxfontcache1                  - X11 font cache extension library
p   libxfontcache1-dbg              - X11 font cache extension library (debug pa
p   memcached                       - A high-performance memory object caching s
p   php-cache-lite                  - Fast and lite data cache system
p   turck-mmcache                   - precompiler and cache to improve performan
p   x11proto-fontcache-dev          - X11 font cache extension wire protocol


This is my sources.list

> # Line commented out by installer because it failed to verify:
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## Dapper PLF
## only uncomment it if you need it
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free


---

### Post by timetunnel on 2006-07-24
```
aptitude search cache mplayer
```
Why do you search for "cache"? This should find it:
```
aptitude search mplayer
```

The package "mplayer" is definitely there, look here:
[MPlayer at packages.ubuntu.com]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mplayer&searchon=names&subword=1&version=dapper&release=all")

---

### Post by Dearhell on 2006-07-24
I know that it should be, but it's not.

---

### Post by Dearhell on 2006-07-24
I can't install neither the rar or the sun-java5-bin package, something is wrong with my repositories and I don't know what 

](*,)

---

### Post by timetunnel on 2006-07-24
What happens if you try it with Synaptic? Or if you switch the servers listed in you sources.list to another one, for example [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) instead of [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) ?

---

### Post by endfx on 2006-07-24
Use this for your sources:

###########################

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

##########################
This was taken from:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Now run:
sudo apt-get update

Now try the mplayer and java packages

---

### Post by Dearhell on 2006-07-24
That has fixed it, it has the same packages than the spanish servers that I've got by default?

---

