---
title: "issues with installing darwinia on 64 bit lucid"
date: 2010-07-24
forum: Gaming &amp; Leisure
---

### Post by akos.maroy on 2010-07-24
Hi,

I'm following the installation guide here: [http://gwos.org/doku.php/guides:64bit:darwinia](http://gwos.org/doku.php/guides:64bit:darwinia)

but after performing these steps, I get:

```

# sh darwinia-complete-1.2.1b.sh 
Verifying archive integrity... All good.
Uncompressing Darwinia complete 1.2.1b.......................................................................
/root/.setup3327: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory

```

and indeed, the libglib1.2-dbg_1.2.10-19build1_i386.deb mentioned in the documentation did not install /usr/lib32/libgmodule-1.2.so.0 :(

what am I missing?


Akos

---

### Post by Perfect Storm on 2010-07-24
Try with this one instead:
[http://packages.ubuntu.com/dapper/i386/libglib1.2/download](http://packages.ubuntu.com/dapper/i386/libglib1.2/download)

---

### Post by akos.maroy on 2010-07-24
> **Artificial Intelligence said:**
> Try with this one instead:
[http://packages.ubuntu.com/dapper/i386/libglib1.2/download](http://packages.ubuntu.com/dapper/i386/libglib1.2/download)

yes, this seems to solve the issue - thanks!

how can I notify the owners of the documentation so that they can update the page?

---

### Post by Perfect Storm on 2010-07-24
You can notify me as I'm written the guides ;)

---

### Post by akos.maroy on 2010-07-24
> **Artificial Intelligence said:**
> You can notify me as I'm written the guides ;)

oh, cool :)

---

### Post by carlbeech on 2010-12-27
Hi,

I'm running 10.10, 64bit, and I tried your link, however this is for 32bit not 64bit, and when running gdebi, I get 'wrong architecture - 32bit'....

Any thoughts? - I miss Darwinia....

Thanks

Carl

---

