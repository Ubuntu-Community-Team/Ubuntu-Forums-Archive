---
title: "Apache install: error $PATH"
date: 2006-01-07
forum: Desktop Environments
---

### Post by kurei on 2006-01-07
When i compiled Apache 2.0.54.I get a error and compiler give up

> 
checking for chosen layout... Apache
checking for working mkdir -p... yes
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
Configuring APR library
Platform: i686-pc-linux-gnuoldld
checking for working mkdir -p... yes
APR Version: 0.9.6
checking for chosen layout... apr
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
configure failed for srclib/apr


I only start to using Linux
I don't know about it
Help me
Thanks

---

### Post by gruepig on 2006-01-08
It looks like you don't have a C compiler installed.  Try 'apt-get install gcc' or select gcc from synaptic.  You might also need make and other devel utils ('apt-get install make').

By the way, is there a particular reason you are compiling apache?  In most cases, you can just install ubuntu's apache package: 'apt-get install apache2'.

---

### Post by ivanp on 2006-10-25
Hi

I'm trying to install the C compiler too. After **installing gcc and make** I got the following error:

```
checking for C compiler default output file name... configure: error: C compiler cannot create executables
```

when trying to compile apache. what **other should I install** too so this compiling and any other goes on?

regards

ivan

---

### Post by ivanp on 2006-10-25
I installed the build-essential packages thru the synaptic manager and then the apache compiling run smoothly

---

