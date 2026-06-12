---
title: "Can not install &quot;libstartup-notification0-dev&quot;"
date: 2005-06-10
forum: Desktop Environments
---

### Post by Nicolinux on 2005-06-10
Hi,

I wanted to try eiciel (nautilus extension to set ACL's) and it needs some libs not installed here. I can't install libstartup-notification0-dev:

```

root@snix:~ # apt-get install libstartup-notification0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libstartup-notification0-dev: Depends: libstartup-notification0 (= 0.8-0ubuntu1) but 0.8-2 is to be installed
E: Broken packages

```

I have libstartup-notification0-0.8-2 installed... So libstartup-notification0 is newer than it's headers and therefore I can't install them? Any idea how to fix it?

Thanks,
Stefan

---

### Post by Ulokye on 2005-06-10
I have the same problem, however I do recall solving a similar problem by using apt-get to get the source and compiling it. i'll get back to you once i get it working :)


//73 Ulokye

---

### Post by willrea on 2005-06-26
I get this:

```
grep: /lib/libattr.la: No such file or directory
/bin/sed: can't read /lib/libattr.la: No such file or directory
libtool: link: `/lib/libattr.la' is not a valid libtool archive
make[2]: *** [libeiciel-nautilus.la] Error 1
make[2]: Leaving directory `/home/will/eiciel-0.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/will/eiciel-0.7'
make: *** [all] Error 2
```

---

