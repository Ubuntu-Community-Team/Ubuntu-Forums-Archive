---
title: "Emerald cannot be installed - E: Broken Packages"
date: 2008-02-08
forum: Desktop Effects &amp; Customization
---

### Post by tom66 on 2008-02-08
```

thomas@orpheus:~$ sudo apt-get install emerald
[sudo] password for thomas:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages
thomas@orpheus:~$ 

```

I get the above error when trying to install Emerald. I recently uninstalled it in an attempt to fix my Compiz, which I eventually achieved. But I can't get it back :(

Please help!
Thanks

PS: I am a bit of a Linux newbie. But I love it! :D

---

### Post by legzelda on 2008-02-08
Open Synaptic and click Edit > Fix Broken Packages and see if it fixes your problem.

---

### Post by tom66 on 2008-02-08
It still throws the same error. But thanks for the suggestion :).

---

### Post by legzelda on 2008-02-08
What happens if you try this?

```
sudo apt-get install libwnck18
```

---

### Post by tom66 on 2008-02-08
It doesn't work:

```

thomas@orpheus:~$ sudo apt-get install libwnck18
[sudo] password for thomas:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libwnck18 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libwnck18 has no installation candidate
thomas@orpheus:~$ 

```

Thanks for the suggestion though... :)

---

### Post by legzelda on 2008-02-08
Search Synaptic for libwnck.  You should find a few results.  Try installing libwnck22, libwnck22-common, and libwnck-dev.  Maybe this time around it won't complain about dependencies?

If you already have them installed, note which version you have.

---

### Post by legzelda on 2008-02-08
If none of those ideas work, there is an Ubuntu .deb of the library from [http://packages.ubuntu.com/feisty/libs/libwnck18](http://packages.ubuntu.com/feisty/libs/libwnck18).  Scroll down to the bottom of the page and select the i386 package.

---

### Post by legzelda on 2008-02-08
There are some packages located at [https://launchpad.net/ubuntu/gutsy/i386/libwnck18](https://launchpad.net/ubuntu/gutsy/i386/libwnck18), too, for a Gutsy installation.  I tried installing the package myself, but it complained about not having libwnck-common, but I have that package installed.  It may involve conflicting version numbers.  Maybe you'll have more luck on your system.

---

### Post by tom66 on 2008-02-09
None of those worked; I either couldn't download them, or the dependencies could not be met... thanks for your help anyway.

---

### Post by moshuptrail on 2008-02-09
Just a thought...  Have you checked your sources.list to make sure things are not commented?

---

### Post by tom66 on 2008-02-12
I uncommented two lines which referred to the restricted parts, but it did not work. :(

---

